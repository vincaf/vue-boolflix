<template>
  <div id="app">
    <HeaderWeb />
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
        }
  },

  methods:{
      getMovies(){
          axios.get('')
          .then((result) => {
              // console.log(result.data.response)
              this.musicAlbumList = result.data.response;
              console.log(this.musicAlbumList);
          })
          .catch((error) => {
              console.warn(error);
          })
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
