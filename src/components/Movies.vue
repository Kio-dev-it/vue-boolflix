<template>
    <main>
        <h2 v-if="movieInfo.length > 0">Movies</h2>
        <ul v-for="elm in movieInfo" :key="elm.id">
            <li>
                <MovieCard :info="elm"/>
            </li>
        </ul>
        <h2 v-if="seriesInfo.length > 0">TV Series</h2>
        <ul v-for="elm in seriesInfo" :key="elm.id">
            <li>
                <MovieCard :info="elm"/>
            </li>
        </ul>
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
            movieInfo: [], 
            seriesInfo: []
        }
    },
    watch:{
        infoSearch: function() {
            
            //call for movie search
            axios
                .get("https://api.themoviedb.org/3/search/movie", {
                    params: {
                        api_key: '5f982b7a134b61a8191ea027b951c118',
                        query: this.infoSearch,
                        language: 'it-IT'
                    }
                }
                )
                .then(
                    (resp)=>{
                        this.movieInfo = resp.data.results;
                    }
                );
            
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

</style>