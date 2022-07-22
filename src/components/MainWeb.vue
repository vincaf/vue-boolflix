<template>
  <main>
    <div class="container">
        <div class="row">
            <div class="col">
                <MoviesList class="py-4" :movies="movies" />
                <SeriesList class="py-4" :series="series" />
            </div>
        </div>
    </div>
  </main>
</template>

<script>
import MoviesList from './MoviesList.vue'
import SeriesList from './SeriesList.vue'

export default {
    name: 'MainWeb',
    components: {
        MoviesList,
        SeriesList,
    },
    props: {
        'movies': {
            required: true,
            type: Array,
        },

        'series': {
            required: true,
            type: Array,
        } 
    },
}
</script>

<style lang="scss" scoped>

</style>