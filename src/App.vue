<template>
  <div id="app">
    <HeaderWeb />
    <MainWeb />
  </div>
</template>

<script>
import HeaderWeb from './components/HeaderWeb.vue'
import MainWeb from './components/MainWeb.vue'

export default {
  name: 'App',
  components: {
    HeaderWeb,
    MainWeb,
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
