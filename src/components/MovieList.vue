<template>
  <div class="movie-list">
    <MovieTile v-for="movie in movies" :key="movie.imdbID" :movie="movie" />
  </div>
</template>

<script>
import { defineComponent } from 'vue';
import MovieTile from './MovieTile.vue';

export default defineComponent({
  name: 'MovieList',
  components: {
    MovieTile
  },
  props: {
    movies: {
      type: Array,
      required: true,
    }
  }
});
</script>

<style scoped>
/* Add movie list styles here */
</style>