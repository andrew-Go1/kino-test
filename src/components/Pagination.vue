<template>
  <div class="pagination">
    <button 
      :disabled="currentPage === 1" 
      @click="changePage(currentPage - 1)"
    >
      Previous
    </button>
    <span>Page {{ currentPage }} of {{ totalPages }}</span>
    <button 
      :disabled="currentPage === totalPages" 
      @click="changePage(currentPage + 1)"
    >
      Next
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Pagination',
  props: {
    currentPage: {
      type: Number,
      required: true,
    },
    totalPages: {
      type: Number,
      required: true,
    },
  },
  methods: {
    changePage(page) {
      this.$emit('pageChanged', page);
    },
  },
});
</script>

<style scoped>
.pagination {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}

button {
  margin: 0 10px;
}
</style>