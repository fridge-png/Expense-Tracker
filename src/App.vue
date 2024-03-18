<template>
  <div id="app">
    <ExpenseForm @add="addExpense" />
    <div class="filter-container">
      <ExpenseFilter @filter="applyFilter" />
    </div>
    <ExpenseList :expenses="filteredExpenses" @delete="deleteExpense" />
  </div>
</template>

<script>
import ExpenseForm from './components/ExpenseForm.vue';
import ExpenseList from './components/ExpenseList.vue';
import ExpenseFilter from './components/ExpenseFilter.vue';
import DeleteExpense from './components/DeleteExpense.vue';

export default {
  components: {
    ExpenseForm,
    ExpenseList,
    ExpenseFilter,
    DeleteExpense
  },
  data() {
    return {
      expenses: [],
      filteredExpenses: []
    };
  },
  methods: {
    addExpense(newExpense) {
      this.expenses.push(newExpense);
      this.applyFilter();
    },
    deleteExpense(expenseToDelete) {
      this.expenses = this.expenses.filter(expense => expense !== expenseToDelete);
      this.applyFilter();
    },
    applyFilter() {
      switch (this.filterCriteria) {
        case 'date':
          this.filteredExpenses = this.expenses.slice().sort((a, b) => new Date(a.date) - new Date(b.date));
          break;
        case 'amount':
          this.filteredExpenses = this.expenses.slice().sort((a, b) => a.amount - b.amount);
          break;
        default:
          this.filteredExpenses = [...this.expenses];
      }
    }
  },
  created() {
    this.filteredExpenses = [...this.expenses];
  }
};
</script>

<style>
#app {
  padding: 20px;
}

.filter-container {
  margin-bottom: 20px;
}
</style>