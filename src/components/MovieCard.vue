<template>
  <div id="MovieCard" class="col-2">
    <img class="w-100" v-if="movie.poster_path == null || movie.poster == ''" src="http://www.movienewz.com/img/films/poster-holder.jpg" :alt="movie.title">
    <img class="w-100" v-else :src="`${this.imgUrl}${movie.poster_path}`" :alt="movie.title">
    <ul class="list-unstyled">
        <li><strong>Titolo:</strong> {{ movie.title }}</li>
        <li><strong>Titolo originale:</strong> {{ movie.original_title }}</li>
        <li v-if="(supportedLanguage.includes(movie.original_language))">
            <strong>Lingua:</strong> <lang-flag :iso="movie.original_language"/>
        </li>
        <li v-else><strong>Lingua:</strong> {{ movie.original_language }}</li>
        <li v-if="movie.vote_average != 0"><strong>Voto: </strong>
            <i v-for="n in 5" :key="n" 
            class="fa-star text-warning"
            :class="n <= getIntegerVote(movie.vote_average) ? 'fa-solid' : 'fa-regular'" ></i>
        </li>
        <li v-else><strong>Voto: </strong> non disponibile</li>
        <li><strong>Panoramica:</strong> {{ movie.overview }}</li>
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

        supportedLanguage: [
                'am', 'az', 'be', 'bn', 'bg', 'zh', 'ca', 'cs', 'en', 'et', 'fr', 'de', 'ha', 'hi', 'hu', 'it', 'ja', 'jv', 'km', 'ko', 'lv', 'ms', 'mr', 'fa', 'pl', 'pt', 'ro', 'ru', 'es', 'sw', 'ta', 'te', 'th', 'tr', 'uz', 'vi',
            ],
        }
    },

    props: {
        'movie': {
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

<style lang="scss" scoped>

    img{
        height: 320px;
    }

    ul{
        display: none;
        margin: 0 auto;
        font-size: 14px;
        padding: 20px;
        background-color: #212529;
        height: 320px;
        overflow: auto;

        li{
            margin: 10px 0;
        }
    }

    #MovieCard{

        height: 320px;

        &:hover{
            img{
                display: none;
            }

            ul{
                display: inline-block;
            }
        }
    }

</style>