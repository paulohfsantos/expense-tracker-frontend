<template>
  <div class="inc-exp-container bg-base-200 flex justify-between p-4 rounded-lg shadow mt-4">
    <div>
      <h4 class="font-semibold">Income</h4>
      <p id="money-plus" class="text-green-500 font-bold">+${{ income }}</p>
    </div>
    <div>
      <h4 class="font-semibold">Expense</h4>
      <p id="money-minus" class="text-red-500 font-bold">-${{ expenses }}</p>
    </div>
  </div>
</template>

<script setup lang="ts">
defineProps({
  income: {
    type: Number,
    required: true,
  },
  expenses: {
    type: Number,
    required: true,
  },
});
</script>