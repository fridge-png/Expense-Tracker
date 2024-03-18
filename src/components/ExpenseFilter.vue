<template>
  <div class="expense-filter">
    <label for="filter" class="filter-label">Filter by:</label>
    <select v-model="filterCriteria" @change="applyFilter" class="filter-select">
      <option value="date">Date</option>
      <option value="amount">Amount</option>
      <!-- Add more filter options as needed -->
    </select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      filterCriteria: 'date'
    };
  },
  methods: {
    applyFilter() {
      this.$emit('filter', this.filterCriteria);
    }
  }
};
</script>

<style scoped>
.expense-filter {
  margin-bottom: 20px;
}
.filter-label {
  font-weight: bold;
  margin-right: 5px; /* Adjusted margin to provide space */
}
.filter-select {
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 4px;
  background-color: #f9f9f9;
  font-size: 14px;
}
</style>