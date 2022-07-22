<template>
  <section>
    <span class="p-2 fs-1 bg-primary text-white">TV SERIES</span>
    <div class="container d-flex flex-wrap">
      <SeriesCard class="m-4" :serie="serie" v-for="(serie, index) in series" :key="index" />
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