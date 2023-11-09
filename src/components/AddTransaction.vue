<template>
  <div class="p-4 rounded-lg shadow">
    <h3 class="text-lg font-semibold mb-4">Add new transaction</h3>
    <form id="form" @submit.prevent="onSubmit" class="space-y-4">
      <div class="form-control">
        <label for="text" class="label">Text</label>
        <input type="text" id="text" placeholder="Enter text..." v-model="text" class="input input-bordered" />
      </div>
      <div class="form-control">
        <label for="amount" class="label">
          Amount <span class="label-text-alt">(negative - expense, positive - income)</span>
        </label>
        <input type="text" id="amount" placeholder="Enter amount..." v-model="amount" class="input input-bordered" />
      </div>
      <button class="btn btn-primary">Add transaction</button>
    </form>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { useToast } from 'vue-toastification';

const toast = useToast();

const text = ref('');
const amount = ref('');

const emit = defineEmits(['transactionSubmitted']);

const onSubmit = () => {
  if (!text.value || !amount.value) {
    toast.error('Both fields must be filled.');
    return;
  }

  const transactionData = {
    text: text.value,
    amount: parseFloat(amount.value),
  };

  emit('transactionSubmitted', transactionData);

  text.value = '';
  amount.value = '';
};
</script>