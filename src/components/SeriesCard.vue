<template>
  <div class="col-2">
    <ul>
        <li>
            <img class="w-100" :src="`${this.imgUrl}${serie.poster_path}`" :alt="serie.title">
        </li>
        <li><strong>Titolo:</strong> {{ serie.name }}</li>
        <li><strong>Titolo originale:</strong> {{ serie.original_name }}</li>
        <li><strong>Lingua:</strong> <lang-flag :iso='serie.original_language' /></li>
        <li><strong>Voto:</strong>
            <i v-for="vote in getIntegerVote(serie.vote_average)" :key="vote" class="fa-solid fa-star ms-1 text-warning"></i>
            <span class="ms-1" v-if="serie.vote_average == 0">Non disponibile</span>
        </li>
        <li><strong>Tipo:</strong> {{ serie.media_type }}</li>
    </ul>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
    name: 'SeriesCard',

    components: {
        LangFlag,
    },

    data: function(){
    return{
        imgUrl: 'https://image.tmdb.org/t/p/w342/',
        }
    },

    props: {
        'serie': {
            required: true,
            type: Object,
        } 
    },

    methods:{
        getIntegerVote(vote){
            return Math.round(vote / 2);
        }
    }
}
</script>

<style>

</style>