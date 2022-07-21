<template>
  <main>
    <div class="container">
        <div class="row">
            <div class="col">
                <MoviesList :movies="movies" />
            </div>
        </div>
    </div>
  </main>
</template>

<script>
import MoviesList from './MoviesList.vue'
export default {
    name: 'MainWeb',
    components: {
        MoviesList,
    },
    props: {
        'movies': {
            required: true,
            type: Array,
        } 
    },
}
</script>

<style lang="scss" scoped>

</style>