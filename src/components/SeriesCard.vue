<template>
  <div id="SeriesCard" class="col-2">
    <img class="w-100" :src="`${this.imgUrl}${serie.poster_path}`" :alt="serie.title">
    <ul class="list-unstyled">
        <li><strong>Titolo:</strong> {{ serie.name }}</li>
        <li><strong>Titolo originale:</strong> {{ serie.original_name }}</li>
        <li v-if="(supportedLanguage.includes(serie.original_language))">
            <strong>Lingua:</strong> <lang-flag :iso="serie.original_language"/>
        </li>
        <li v-else><strong>Lingua:</strong> {{ serie.original_language }}</li>
        <li v-if="serie.vote_average != 0"><strong>Voto: </strong>
            <i v-for="n in 5" :key="n" 
            class="fa-star text-warning"
            :class="n <= getIntegerVote(serie.vote_average) ? 'fa-solid' : 'fa-regular'" ></i>
        </li>
        <li v-else><strong>Voto: </strong> non disponibile</li>
        <li><strong>Panoramica:</strong> {{ serie.overview }}</li>
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

        supportedLanguage: [
                'am', 'az', 'be', 'bn', 'bg', 'zh', 'ca', 'cs', 'en', 'et', 'fr', 'de', 'ha', 'hi', 'hu', 'it', 'ja', 'jv', 'km', 'ko', 'lv', 'ms', 'mr', 'fa', 'pl', 'pt', 'ro', 'ru', 'es', 'sw', 'ta', 'te', 'th', 'tr', 'uz', 'vi',
            ],
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

<style lang="scss" scoped>

    ul{
        display: none;
        margin: 0 auto;
        font-size: 14px;
        padding: 20px;
        background-color: #212529;
        height: 310px;
        overflow: auto;

        li{
            margin: 10px 0;
        }
    }

    #SeriesCard{

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