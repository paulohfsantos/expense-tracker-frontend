<template>
  <div class="container mx-auto p-6">
    <balance :total="total" />

    <income-expenses :income="+income" :expenses="+expenses" />

    <transaction-list
      :transactions="transactions"
      @transactionDeleted="handleTransactionDeleted"
    />
    <add-transaction @transactionSubmitted="handleTransactionSubmitted" />
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';
import Balance from '@/components/Balance.vue';
import IncomeExpenses from '@/components/IncomeExpenses.vue';
import AddTransaction from '@/components/AddTransaction.vue';
import TransactionList from '@/components/TransactionList.vue';
import { useToast } from 'vue-toastification';
import type { Transaction, TransactionData } from '@/types';

const toast = useToast();

const transactions = ref<Transaction[]>([]);

// Get total
const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0);
});

// Get income
const income = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, transaction) => acc + transaction.amount, 0)
    .toFixed(2);
});

// Get expenses
const expenses = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, transaction) => acc + transaction.amount, 0)
    .toFixed(2);
});

// Submit transaction
const handleTransactionSubmitted = (transaction: Transaction) => {
  transactions.value.push({
    id: generateUniqueId(),
    text: transaction.text,
    amount: transaction.amount,
  });

  saveTransaction(transaction);

  toast.success('Transaction added.');
};

// Generate unique ID
const generateUniqueId = () => {
  return Math.floor(Math.random() * 10);
};

const handleTransactionDeleted = (id: number) => {
  console.log('id', id);
};

const handleTransaction = (transactionData: TransactionData) => {
  console.log('transactionData', transactionData);
};

const saveTransaction = (transaction: Transaction) => {
  transactions.value.push(transaction);

  console.log('transactions', transactions.value);
};
</script>