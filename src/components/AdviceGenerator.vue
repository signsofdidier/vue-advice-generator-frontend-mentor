<script setup>
import axios from 'axios';
import { onMounted, ref } from 'vue';

import divider_desktop from '@/assets/images/pattern-divider-desktop.svg';
import divider_mobile from '@/assets/images/pattern-divider-mobile.svg';
import dice_icon from '@/assets/images/icon-dice.svg';

const advice = ref(null);
const adviceId = ref(null);
const loading = ref(false);
const error = ref(null);

const getAdvice = async () => {
  loading.value = true;
  error.value = null;

  try {
    const response = await axios.get(
      `https://api.adviceslip.com/advice?timestamp=${Date.now()}`
    );
    advice.value = response.data.slip.advice;
    adviceId.value = response.data.slip.id;
  } catch (err) {
    error.value = err.message;
  } finally {
    loading.value = false;
  }
};

onMounted(() => {
  getAdvice();
});
</script>

<template>
  <!-- Advice Generator -->
  <div
    class="max-w-lg p-10 m-6 md:m-0 bg-blue-2 rounded-xl flex flex-col justify-center text-center space-y-6 relative"
  >
    <!-- <h2>{{ advice }}</h2> -->
    <!-- Advice ID -->
    <h2 class="text-secondary tracking-[5px] uppercase font-semibold">
      Advice #{{ adviceId }}
    </h2>

    <!-- Quote -->
    <div>
      <!-- <p v-if="loading">Loading...</p> -->
      <p v-if="error" class="text-red-500 font-bold text-quote">
        Error: {{ error }}
      </p>
      <p v-else class="text-primary font-bold text-quote">
        &quot;{{ advice }}&quot;
      </p>
    </div>

    <!-- divider -->
    <div class="mt-2">
      <img
        class="hidden md:block w-full"
        :src="divider_desktop"
        alt="divider"
      />
      <img class="md:hidden" :src="divider_mobile" alt="divider" />
    </div>

    <button
      @click="getAdvice()"
      class="absolute bottom-0 right-1/2 translate-x-1/2 translate-y-1/2 bg-secondary w-15 h-15 rounded-full flex items-center justify-center hover:shadow-[0px_0px_30px_0px] hover:shadow-secondary transition duration-200 ease-in-out cursor-pointer"
    >
      <img :src="dice_icon" alt="dice icon" />
    </button>
  </div>
</template>

<style scoped></style>
