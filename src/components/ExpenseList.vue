<template>
  <div class="expense-list">
    <h2>Expense List</h2>
    <ul>
      <li v-for="(expense, index) in expenses" :key="index">
        {{ expense.description }} - ${{ expense.amount.toFixed(2) }}
        <DeleteExpense :expense="expense" @delete="deleteExpense" />
      </li>
    </ul>
  </div>
</template>

<script>
import DeleteExpense from './DeleteExpense.vue';

export default {
  props: ['expenses'],
  components: {
    DeleteExpense
  },
  methods: {
    deleteExpense(expenseToDelete) {
      this.$emit('delete', expenseToDelete);
    }
  }
};
</script>

<style scoped>
.expense-list {
  margin-bottom: 20px;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin-bottom: 5px;
}
</style>