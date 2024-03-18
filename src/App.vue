<template>
  <div id="app">
    <ExpenseForm @add="addExpense" />
    <ExpenseList :expenses="expenses" />
  </div>
</template>

<script>
import ExpenseForm from './components/ExpenseForm.vue';
import ExpenseList from './components/ExpenseList.vue';

export default {
  components: {
    ExpenseForm,
    ExpenseList
  },
  data() {
    return {
      expenses: []
    };
  },
  methods: {
    addExpense(newExpense) {
      this.expenses.push(newExpense);
    }
  }
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  margin: 0 auto;
  padding: 20px;
  max-width: 600px;
}
</style>