<script setup lang="ts">
import HomePage from './views/Home.vue'
import NavMenu from './components/NavMenu.vue';
</script>

<template>
  <nav-menu />

  <main>
    <section class="flex justify-center">
      <div class="w-1/2">
        <home-page />
      </div>
    </section>
  </main>
</template>
