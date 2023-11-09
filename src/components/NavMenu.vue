<template>
  <header class="p-3 navbar bg-base-200">
    <div class="flex-1">
      <h1 class="text-lg font-semibold">
        Expense Tracker
      </h1>
    </div>
    <div class="flex-none">
      <div class="px-3">
        <select data-choose-theme class="select select-bordered w-full max-w-xs select-sm">
          <option v-for="theme in themes" :value="theme" :key="theme">
            {{ theme }}
          </option>
        </select>
      </div>
    </div>
  </header>
</template>

<script setup lang="ts">
import { onMounted } from 'vue';
import { themeChange } from 'theme-change';
import { themes } from '../utils/themes';

onMounted(() => {
  themeChange(false);
});
</script>
