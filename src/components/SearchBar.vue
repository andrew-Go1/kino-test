<template>
  <div class="search-bar">
    <input v-model="searchQuery" @keyup.enter="search" placeholder="Search for movies...">
    <button @click="search">Search</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'SearchBar',
  setup(props, { emit }) {
    const searchQuery = ref('');

    const search = () => {
      emit('search', searchQuery.value);
    };

    return { searchQuery, search };
  },
});
</script>

<style scoped>
/* Add search bar styles here */
</style>