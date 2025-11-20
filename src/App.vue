<script setup>
import Layout from './Layouts/Layout.vue';

import divider_desktop from './assets/images/pattern-divider-desktop.svg';
import divider_mobile from './assets/images/pattern-divider-mobile.svg';
import dice_icon from './assets/images/icon-dice.svg';
</script>

<template>
  <Layout>
    <!-- Advice Generator -->
    <div
      class="max-w-lg p-10 m-6 md:m-0 bg-blue-2 rounded-xl flex flex-col justify-center text-center space-y-6 relative"
    >
      <!-- Advice ID -->
      <h2 class="text-secondary tracking-[5px] uppercase font-semibold">
        Advice #id
      </h2>

      <!-- Quote -->
      <p class="text-primary font-bold text-quote">
        &quot;Its bla bla ben nog een bla want dit vul ik later wel in
        seg.&quot;
      </p>

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
        class="absolute bottom-0 right-1/2 translate-x-1/2 translate-y-1/2 bg-secondary w-15 h-15 rounded-full flex items-center justify-center hover:shadow-[0px_0px_30px_0px] hover:shadow-secondary transition duration-200 ease-in-out cursor-pointer"
      >
        <img :src="dice_icon" alt="dice icon" />
      </button>
    </div>
  </Layout>
</template>

<style scoped></style>
<!-- absolute bottom-0 right-1/2 translate-x-1/2 translate-y-1/2 -->
