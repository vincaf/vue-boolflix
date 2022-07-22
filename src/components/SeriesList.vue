<template>
  <div class="d-flex flex-wrap justify-content-center">
    <SeriesCard class="m-4" :serie="serie" v-for="(serie, index) in series" :key="index" />
  </div>
</template>

<script>
import SeriesCard from './SeriesCard.vue'
export default {
    name: 'SeriesList',
    components: {
        SeriesCard,
    },
    props: {
        'series': {
            required: true,
            type: Array,
        } 
    },
}
</script>

<style>

</style>