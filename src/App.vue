<template>
  <div id="app">
    <Header @search="searchMovies" />
    <main>
      <div class="search-info" v-if="searchQuery">
        <p>You searched for: {{ searchQuery }},</p>
        <p>{{ totalResults }} results found</p>
      </div>
      <Loader v-if="loading" />
      <NoResults v-else-if="!loading && movies.length === 0" />
      <MovieList v-else :movies="movies" />
      <Pagination 
        v-if="totalResults > 10"
        :currentPage="currentPage"
        :totalPages="Math.ceil(totalResults / 10)"
        @pageChanged="changePage"
      />
    </main>
  </div>
</template>

<script>
import { defineComponent, ref } from 'vue';
import axios from 'axios';
import Header from './components/Header.vue';
import MovieList from './components/MovieList.vue';
import Loader from './components/Loader.vue';
import NoResults from './components/NoResults.vue';
import Pagination from './components/Pagination.vue';

export default defineComponent({
  name: 'App',
  components: {
    // eslint-disable-next-line vue/no-reserved-component-names
    Header,
    MovieList,
    Loader,
    NoResults,
    Pagination,
  },
  setup() {
    const movies = ref([]);
    const loading = ref(false);
    const searchQuery = ref('');
    const totalResults = ref(0);
    const currentPage = ref(1);

    const searchMovies = async (query, page = 1) => {
      loading.value = true;
      searchQuery.value = query;
      currentPage.value = page;
      try {
        const response = await axios.get(`https://www.omdbapi.com/?apikey=8523cbb8&s=${query}&page=${page}`);
        movies.value = response.data.Search || [];
        totalResults.value = parseInt(response.data.totalResults) || 0;
      } catch (error) {
        console.error('Error fetching movies:', error);
      } finally {
        loading.value = false;
      }
    };

    const changePage = (page) => {
      searchMovies(searchQuery.value, page);
    };

    return {
      movies,
      loading,
      searchQuery,
      totalResults,
      currentPage,
      searchMovies,
      changePage,
    };
  },
});
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  max-width: 100vw;
  margin: 0 auto;
}

main {
  margin: 20px;
}

.search-info {
  display: flex;
  margin-bottom: 20px;
  p {
    margin-right: 2pt;
  }
}
</style>