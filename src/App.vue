<template>
  <div id="app">
    <HeaderWeb @search="getMovies" />
    <MainWeb />
  </div>
</template>

<script>
import HeaderWeb from './components/HeaderWeb.vue';
import MainWeb from './components/MainWeb.vue';
// import axios from 'axios';

export default {
  name: 'App',

  components: {
    HeaderWeb,
    MainWeb,
  },

  data: function(){
        return{
            moviesList: [],
        }
  },

  methods:{
      getMovies(search){
        console.log(search);
      },
  }
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
