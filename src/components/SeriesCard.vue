<template>
  <div id="SeriesCard" class="col-2">
    <img class="w-100" v-if="serie.poster_path == null || serie.poster == ''" src="http://www.movienewz.com/img/films/poster-holder.jpg" :alt="serie.name">
    <img class="w-100" v-else :src="`${this.imgUrl}${serie.poster_path}`" :alt="serie.name">
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
        <div class="text-center">
            <button @click="getCast(serie.id)" class="my-2 btn btn-outline-secondary">Scopri il cast</button>
            <li v-for="member in cast" :key="member.id" class="mt-2"> {{member.name}} </li>
        </div>
    </ul>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
import axios from 'axios';

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

        cast: [],
        apiKey: '88ad43231db09cad59cba4c08bf2d037',
        apiUrl: 'https://api.themoviedb.org/3/movie/',
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
        },

        getCast(id){
            axios.get(`${this.apiUrl}${id}/credits?api_key=${this.apiKey}`)
            .then(result => {
                this.cast = result.data.cast;
                this.cast.splice(5);
                console.log(this.cast);
            })
            .catch(error => {
                console.log(error);
            });
        },
    }
}
</script>

<style lang="scss" scoped>

#SeriesCard{
    height: 320px;

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

    button{
        font-size: 14px;
    }

    &:hover{
        transform: scale(1.1);
        transition: transform 0.8s;

        img{
            display: none;
        }

        ul{
            display: inline-block;
        }
    }
}

</style>