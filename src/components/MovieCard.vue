<template>
    <div class="card">

            <img :src="`https://image.tmdb.org/t/p/w342${info.poster_path}`" alt="" class="card__image">

            <!-- there is two v-if to manage the different key in obj movie and obj series about titles -->

            <div class="card__movie" v-if="info.original_title">
                <div><strong>Titolo:</strong>{{info.title}}</div>
                <div><strong>Titolo orginale:</strong>{{info.original_title}}</div>
            </div>
            <div class="card__series" v-if="info.original_name">
                <div><strong>Titolo:</strong>{{info.name}}</div>
                <div><strong>Titolo orginale:</strong>{{info.original_name}}</div>
            </div>
            <div><strong>lingua:</strong><lang-flag :iso="info.original_language" :squared="false"/></div>
            <div><strong>Voto:</strong><font-awesome-icon :icon="starSolid" v-for="elm in starMaker()" :key="elm"/><font-awesome-icon :icon="starEmpty" v-for="elm in 5 - starMaker()" :key="elm"/></div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import { faStar as fasStar } from '@fortawesome/free-solid-svg-icons';
import { faStar as farStar } from '@fortawesome/free-regular-svg-icons';


export default {
    name: 'MovieCard',
    props:['info'],
    components:{
        LangFlag,
        FontAwesomeIcon,
    }, 
    data() {
        return {
            vote: 0,
            starSolid: fasStar,
            starEmpty: farStar
        }
    },
    methods:{
        starMaker() {
            return Math.ceil(this.info.vote_average / 2);
        }
    }
}
</script>

<style lang="scss" scoped>

</style>