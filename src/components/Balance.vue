<template>
  <div>
    <h4>Your Balance</h4>

    <span>{{ finalTotal }}</span>
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