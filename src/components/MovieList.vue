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
.movie-list {
  display: grid;
  max-width: 1200px;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1rem;
}

@media (max-width: 768px) {
  .movie-list {
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  }
}

@media (max-width: 480px) {
  .movie-list {
    grid-template-columns: 1fr;
  }
}
</style>