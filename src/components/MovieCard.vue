<template>
    <div class="movie-card">
            <div><strong>Titolo:</strong>{{info.title}}</div>
            <div><strong>Titolo orginale:</strong>{{info.original_title}}</div>
            <div><strong>lingua:</strong><lang-flag :iso="info.original_language" :squared="false"/></div>
            <div><strong>Voto:</strong>{{info.vote_average}}</div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    name: 'MovieCard',
    props:['info'],
    components:{
        LangFlag
    }
}
</script>

<style lang="scss" scoped>

</style>