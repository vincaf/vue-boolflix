<template>
  <div id="app">
    <HeaderWeb @search="getMedias" />
    <MainWeb :movies="moviesList" :series="seriesList" :message="message" />
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
        message: 'Benvenuto! qui potrai cercare facilmente i tuoi film e serie tv preferiti, inserisci cosa vuoi cercare per iniziare.',
    }
  },

  methods:{
    getMedias(search){
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
          } else if(element.media_type == 'tv'){
            this.seriesList.push(element);
          }

          this.message = 'Nessun risultato di ricerca trovato.'
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

body{
  background-color: #434343;
  color: #fff;
}

::-webkit-scrollbar {
  height: 2px;
}

::-webkit-scrollbar-track {
  background: #282828;
}

::-webkit-scrollbar-thumb {
  background: #707070;
}
</style>
