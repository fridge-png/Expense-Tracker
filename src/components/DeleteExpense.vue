<template>
  <button @click="deleteExpense" class="delete-btn">Delete</button>
</template>

<script>
export default {
  props: ['expense'],
  methods: {
    deleteExpense() {
      this.$emit('delete', this.expense);
    }
  }
};
</script>

<style scoped>
.delete-btn {
  padding: 5px 10px;
  background-color: #dc3545;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
.delete-btn:hover {
  background-color: #c82333;
}
</style>