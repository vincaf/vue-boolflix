<template>
  <div id="app">
    <HeaderWeb @search="getMovies" />
    <MainWeb />
  </div>
</template>

<script>
import HeaderWeb from './components/HeaderWeb.vue';
import MainWeb from './components/MainWeb.vue';
import axios from 'axios';

export default {
  name: 'App',

  components: {
    HeaderWeb,
    MainWeb,
  },

  data: function(){
    return{
        moviesList: [],
        apiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=59c53a96f763c9716248c35c07d50ee0&language=it-IT&query=',
    }
  },

  methods:{
    getMovies(search){
      console.log(search);
      this.apiUrl = this.apiUrl + search;
      console.log(this.apiUrl);
      axios.get(this.apiUrl)
      .then( (result) => {
        this.moviesList = result.data.results;
        console.log(this.moviesList);
        this.apiUrl = 'https://api.themoviedb.org/3/search/movie?api_key=59c53a96f763c9716248c35c07d50ee0&language=it-IT&query=';
      })
      .catch((error) => {
        console.warn(error);
      })
    },
  },
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
