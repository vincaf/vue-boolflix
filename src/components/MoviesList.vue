<template>
  <section>
    <span class="p-2 fs-1 bg-dark text-white">MOVIES</span>
    <div class="container d-flex overflow-auto">
      <MovieCard class="my-5 mx-1" :movie="movie" v-for="movie in movies" :key="movie.id" />
    </div>
  </section>
</template>

<script>
import MovieCard from './MovieCard.vue'
export default {
    name: 'MoviesList',
    components: {
        MovieCard,
    },
    props: {
        'movies': {
            required: true,
            type: Array,
        } 
    },
}
</script>

<style>

</style>