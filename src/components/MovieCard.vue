<template>
    <div class="card mx-auto">
            <div class="card__image">
                
                <img v-if="info.poster_path" :src="`https://image.tmdb.org/t/p/w342${info.poster_path}`" :alt="info.original_title || info.original_name" class="card__image">
                <div v-else class="card__image__replace">
                    <h5>Ci scusiamo per il disagio, ma non disponiamo del poster di <span class="title">"{{info.original_title || info.original_name}}"</span></h5>
                    <p>Team <span>BOOLFLIX</span></p>
                </div>
            </div>

            <div class="card__info">
                <div class="card__movie">
                    <div><strong>Titolo:</strong> {{info.title || info.name}}</div>
                    <!-- i use this v-if to avoid showing the title of the show if it is the same as the original one -->
                    <div v-if="info.title !== info.original_title || info.name !== info.original_name"><strong>Titolo orginale:</strong> {{info.original_title || info.original_name}}</div>
                </div>
                <div><strong>Lingua:</strong><lang-flag :iso="info.original_language" :squared="true"/></div>
                <div><strong>Voto:</strong> <font-awesome-icon :icon="starSolid" v-for="elm in starMaker()" :key="elm"/><font-awesome-icon :icon="starEmpty" v-for="elm in starDestroyer()" :key="elm"/></div>
            </div>
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
            starSolid: fasStar,
            starEmpty: farStar
        }
    },
    methods:{
        consecArrMaker(min, max) {
            const arrStar = [];
            for (let i = min; i < max; i++){
                arrStar.push(i);
            }
            return arrStar;
        },
        starMaker() {
            return this.consecArrMaker(0, Math.ceil( this.info.vote_average / 2 ));
        },
        starDestroyer(){
            return this.consecArrMaker( Math.ceil( this.info.vote_average / 2 ), 5);
        }

    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/variables.scss';


    .card{
        position: relative;
        color: #fff;
        max-width: 14rem;
        height: calc(14rem * 1.5);

        &__image{
            height: 100%;
            z-index: 1;
            opacity: 1;
            transition: opacity .3s ease-in-out;

            &:hover{
                opacity: 0;
            }

            img{
                width: 100%;
                height: 100%;
                object-fit: cover;
            }

            &__replace{
                padding: .625rem;
                background-color: $mainBgColor;
                position: relative;
                height: 100%;

                .title{
                    display: block;
                    font-weight: 700;
                    margin-top: 8px;
                    text-align: center;
                }

                p{
                    text-align: center;
                    position: absolute;
                    right: .875rem;
                    bottom: 3.125rem;
                    font-size: 1.25rem;

                    span{
                        color: $mainTextColor;
                        display: block;
                        font-weight: 900;
                    }
                }
            }
        }


        &__info{
            padding: .625rem;
            position: absolute;
            top:0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: $mainBgColor;

            .flag-icon{
                margin-left: .5rem;
                border-radius: 50%;
            }
        }
    }

    @media screen and (max-width: 576.1px){
        .card{
            height: calc(320px * 1.5);
            max-width: 320px;

            &__image__replace{
                padding-top: 25px;

            }
        }
    
    }


</style>