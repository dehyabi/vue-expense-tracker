<template>
  <div class="text-center">
    <h4>Your Balance</h4>
    <h1>${{ total }}</h1>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});
</script>
