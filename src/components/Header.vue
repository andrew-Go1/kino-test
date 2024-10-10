<template>
  <header>
    <h1>Movie Catalog</h1>
    <SearchBar @search="onSearch" />
    <UserInfo />
  </header>
</template>

<script>
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
  width: 100%;
  padding: 20px;
  background-color: rgb(28, 56, 56);
}
</style>