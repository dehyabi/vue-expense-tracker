<template>
  <div
    class="flex flex-row gap-20 border border-radius-20 p-10 justify-center bg-white"
  >
    <div>
      <h4>Income</h4>
      <p id="moneyPlus" class="green">+${{ income }}</p>
    </div>
    <div>
      <h4>Expense</h4>
      <p id="moneyMinus" class="red">-${{ expenses }}</p>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
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
