<template>
  <div class="flex flex-col justify-center align-items-center h-100-vh">
    <div class="border border-radius-20 p-50 container of-auto">
      <Header />
      <Balance :total="total"/>
      <IncomeExpenses :income="income" :expenses="expenses" />
      <TransactionList :transactions="transactions" />
      <AddTransaction />
    </div>
  </div>
</template>

<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpenses from "./components/IncomeExpenses.vue";
import TransactionList from "./components/TransactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";

import { ref, computed } from "vue";

const transactions = ref([
  { id: 1, text: "Food", amount: -5.9 },
  { id: 2, text: "Salary", amount: 2500 },
  { id: 3, text: "Snack", amount: -3.87 },
  { id: 4, text: "Holiday", amount: -300.87 },
]);

// get total
const total = computed(() => {
  return transactions.value.reduce((acc, transaction)=> {
    return acc + transaction.amount
  }, 0)
});

// get income
const income = computed(() => {
  return transactions.value
  .filter((transaction) => transaction.amount > 0)
  .reduce((acc, transaction)=> {
    return acc + transaction.amount
  }, 0).toFixed(2)
});

// get expense
const expenses = computed(() => {
  return transactions.value
  .filter((transaction) => transaction.amount < 0)
  .reduce((acc, transaction)=> {
    return acc + transaction.amount
  }, 0).toFixed(2)
});
</script>
