<script setup lang="ts">
import HomePage from './views/Home.vue'
import NavMenu from './components/NavMenu.vue';
</script>

<template>
  <nav-menu />

  <main>
    <!-- <div class="hero min-h-screen bg-base-200">
      <div class="hero-content">
        <div class="max-w-xl">
          <home-page />
        </div>
      </div>
    </div> -->
    <section class="flex justify-center">
      <div class="w-1/2">
        <home-page />
      </div>
    </section>
  </main>
</template>
