<template>
  <header>
    <h1>Movie Search</h1>
    <SearchBar @search="onSearch" />
    <UserInfo />
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SearchBar from './SearchBar.vue';
import UserInfo from './UserInfo.vue';

export default defineComponent({
  // eslint-disable-next-line vue/multi-word-component-names, vue/no-reserved-component-names
  name: 'Header',
  components: {
    SearchBar,
    UserInfo,
  },
  methods: {
    onSearch(query) {
      this.$emit('search', query);
    },
  },
});
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 0;
}
</style>