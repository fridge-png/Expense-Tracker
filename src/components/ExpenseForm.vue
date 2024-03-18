<template>
  <div class="expense-form">
    <h2>Add New Expense</h2>
    <form @submit.prevent="addExpense">
      <div class="form-group">
        <label for="description">Description:</label>
        <input type="text" id="description" v-model="description" required>
      </div>
      <div class="form-group">
        <label for="amount">Amount:</label>
        <input type="number" id="amount" v-model.number="amount" required>
      </div>
      <button type="submit">Add Expense</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      description: '',
      amount: null
    };
  },
  methods: {
    addExpense() {
      if (!this.description || !this.amount) return;
      this.$emit('add', {
        description: this.description,
        amount: parseFloat(this.amount)
      });
      this.description = '';
      this.amount = null;
    }
  }
};
</script>

<style scoped>
.expense-form {
  margin-bottom: 20px;
}
.form-group {
  margin-bottom: 10px;
}
label {
  display: block;
  font-weight: bold;
}
input[type="text"],
input[type="number"] {
  width: 100%;
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 4px;
}
button {
  padding: 8px 20px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
button:hover {
  background-color: #0056b3;
}
</style>