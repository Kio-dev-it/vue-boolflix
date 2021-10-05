<template>
    <main>
        <MovieCard :info="movieInfo"/>
    </main>
</template>

<script>
import axios from 'axios';
import MovieCard from './MovieCard.vue';

export default {
    name: 'Movies',
    components: {
        MovieCard
    },
    data() {
        return {
            movieInfo: []
        }
    },
    created(){
        axios
            .get("https://api.themoviedb.org/3/search/movie?", {
                params: {
                    api_key: '5f982b7a134b61a8191ea027b951c118',
                    query: 'ritorno al futuro'
                }
            }
            )
            .then(
                (resp)=>{
                    this.movieInfo = resp.data.results;
                    console.log(this.movieInfo);
                }
            )

    }
}
</script>

<style lang="scss" scoped>

</style>