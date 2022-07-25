<template>
  <section>
    <span class="p-2 fs-1 bg-dark text-white">TV SERIES</span>
    <div class="container d-flex overflow-auto">
      <SeriesCard class="m-4" :serie="serie" v-for="serie in series" :key="serie.id" />
    </div>
  </section>
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