<template>
  <div id="app">
    <HeaderWeb @search="getMovies" />
    <MainWeb :movies="moviesList" :series="seriesList" />
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
        mediaAllList: [],
        moviesList: [],
        seriesList: [],
        apiKey: '88ad43231db09cad59cba4c08bf2d037',
        apiUrl: 'https://api.themoviedb.org/3/search/multi',
    }
  },

  methods:{
    getMovies(search){
      console.log(search);
      this.moviesList = [];
      this.seriesList = [],

      axios.get(`${this.apiUrl}?api_key=${this.apiKey}&language=it-IT&query=${search}`)
      .then( (result) => {
        this.mediaAllList = result.data.results;
        console.log(this.mediaAllList);

        this.mediaAllList.forEach(element => {
          if(element.media_type == 'movie'){
            this.moviesList.push(element);
          } else {
            this.seriesList.push(element);
          }
        });

        console.log(this.moviesList);
        console.log(this.seriesList);
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
