<template>
  <div>
    <h3>History</h3>
    <div
      v-for="transaction in transactions"
      :key="transaction.id"
      class="mb-10"
    >
      <div
        class="flex justify-between align-items-center list"
        :class="transaction.amount < 0 ? 'minus' : 'plus'"
      >
        <div>
          <span
            ><svg
              class="x-btn"
              data-slot="icon"
              fill="none"
              stroke-width="1.5"
              stroke="currentColor"
              viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg"
              aria-hidden="true"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="m9.75 9.75 4.5 4.5m0-4.5-4.5 4.5M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z"
              ></path></svg
          ></span>
          <span class="list-item">{{ transaction.text }}</span>
        </div>
        <div>${{ transaction.amount }}</div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  },
});
</script>

<style lang="scss">
.list:hover {
  .x-btn {
    opacity: 1;
  }
}

.x-btn {
  color: rgb(248, 67, 67);
  width: 20px;
  vertical-align: bottom;
  margin-left: -32px;
  opacity: 0;
}
</style>
