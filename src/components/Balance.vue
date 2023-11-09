<template>
  <div class="p-4 rounded-lg bg-base-200 mt-4">
    <h4 class="font-semibold">Your Balance</h4>
    <span class="text-xl font-bold">{{ finalTotal }}</span>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue';
import { currencyFormatter } from '../utils/currencyFormatter';

const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
})

const finalTotal = computed(() => {
  console.log('finalTotal computed', props.total);
  return currencyFormatter(props.total);
});
</script>