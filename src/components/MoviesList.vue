<template>
  <div class="d-flex flex-wrap justify-content-center">
    <movieCard class="m-4" :movie="movie" v-for="(movie, index) in movies" :key="index" />
  </div>
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