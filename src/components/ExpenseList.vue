<template>
  <div class="expense-list">
    <h2>Expense List</h2>
    <ul>
      <li v-for="(expense, index) in expenses" :key="index">
        {{ expense.description }} - ${{ expense.amount.toFixed(2) }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['expenses']
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