<template>
    <main>
        <h2 v-if="seriesInfo.length > 0">TV Series</h2>
        <div class="row row-cols-xl-5 container mx-auto">
            <div v-for="elm in seriesInfo" :key="elm.id" class="col-12 col-sm-6 col-md-4 col-lg-3 col-xl p-2">

                <MovieCard :info="elm"/>

            </div>
        </div>
    </main>
</template>

<script>
import axios from 'axios';
import MovieCard from './MovieCard.vue';

export default {
    name: 'Movies',
    props: ['infoSearch'],
    components: {
        MovieCard
    },
    data() {
        return {
            seriesInfo: []
        }
    },
    watch:{
        infoSearch: function() {
            
            //call for TV series search
            axios
                .get("https://api.themoviedb.org/3/search/tv", {
                    params: {
                        api_key: '5f982b7a134b61a8191ea027b951c118',
                        query: this.infoSearch,
                        language: 'it-IT'
                    }
                }
                )
                .then(
                    (resp)=>{
                        this.seriesInfo = resp.data.results;
                    }
                )
        }
    }
}
</script>

<style lang="scss" scoped>
    
    main{
        padding-top: 16px;
        
        h2{
            text-align: center;
            color:#fff;
        }

    }
</style>