<template>
  <div class="mt-4 p-4 bg-base-200">
    <h3 class="text-lg font-semibold mb-2">History</h3>
    <ul id="list" class="list-none">
      <li
        v-for="transaction in transactions"
        :key="transaction.id"
        :class="transaction.amount < 0 ? 'bg-red-400' : 'bg-green-400'"
        class="flex justify-between items-center p-3 mb-2 rounded"
      >
        <span>{{ transaction.text }}</span>
        <span>${{ transaction.amount }}</span>

        <button
          class="btn btn-error btn-xs"
          @click="deleteTransaction(transaction.id)"
        >
          x
        </button>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import type { PropType } from 'vue';
import type { Transaction } from '@/types';

defineProps({
  transactions: {
    type: Array as PropType<Transaction[]>,
    required: true,
  },
});

const emit = defineEmits(['transactionDeleted']);

const deleteTransaction = (id: number) => {
  emit('transactionDeleted', id);
};
</script>