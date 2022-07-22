<template>
  <div class="col-2">
    <ul>
        <li>
            <img class="w-100" :src="`${this.imgUrl}${movie.poster_path}`" :alt="movie.title">
        </li>
        <li><strong>Titolo:</strong> {{ movie.title }}</li>
        <li><strong>Titolo originale:</strong> {{ movie.original_title }}</li>
        <li><strong>Lingua:</strong> <lang-flag :iso='movie.original_language' /></li>
        <li><strong>Voto:</strong> {{ movie.vote_average }}</li>
        <li><strong>Tipo:</strong> {{ movie.media_type }}</li>
    </ul>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
    name: 'MovieCard',

    components: {
        LangFlag,
    },

    data: function(){
    return{
        imgUrl: 'https://image.tmdb.org/t/p/w342/',
        }
    },

    props: {
        'movie': {
            required: true,
            type: Object,
        } 
    },
}
</script>

<style>

</style>