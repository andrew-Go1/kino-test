<template>
  <div class="movie-tile">
    <img :src="posterUrl" :alt="movie.Title" width="100%">
    <h3>{{ movie.Title }}</h3>
    <p>Year: {{ movie.Year }}</p>
    <p>ID: {{ movie.imdbID }}</p>
    <p>Type: {{ movie.Type }}</p>
  </div>
</template>

<script>
import { defineComponent, computed } from 'vue';

export default defineComponent({
  name: 'MovieTile',
  props: {
    movie: {
      type: Object,
      required: true,
    },
  },
  setup(props) {
    const posterUrl = computed(() => {
      return props.movie.Poster !== 'N/A' ? props.movie.Poster : 'path/to/placeholder-image.jpg';
    });

    return { posterUrl };
  },
});
</script>

<style scoped>
/* Add movie tile styles here */
</style>