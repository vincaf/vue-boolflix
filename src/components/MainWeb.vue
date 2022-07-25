<template>
  <main>
    <div class="container">
        <div class="row">
            <div class="col">
                <MoviesList class="py-4" :movies="movies" v-if="movies.length" />
                <SeriesList class="py-4" :series="series" v-if="series.length" />
            </div>
        </div>

        <h1 class="text-center text-white mt-4" v-if="movies.length===0 && series.length===0">
            {{this.message}}
        </h1>
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
        },
        
        'message': {
            required: true,
            type: String,
        }
    },
}
</script>

<style lang="scss" scoped>

</style>