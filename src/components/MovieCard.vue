<template>
    <div class="card">
            <div class="card__movie" v-if="info.original_title">
                <div><strong>Titolo:</strong>{{info.title}}</div>
                <div><strong>Titolo orginale:</strong>{{info.original_title}}</div>
            </div>
            <div class="card__series" v-if="info.original_name">
                <div><strong>Titolo:</strong>{{info.name}}</div>
                <div><strong>Titolo orginale:</strong>{{info.original_name}}</div>
            </div>
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