<template>
    <div class="movie-card">
        <ul v-for="(elm, index) in info" :key="index">
            <li><strong>Titolo:</strong> {{elm.title}}</li>
            <li><strong>Titolo orginale:</strong> {{elm.original_title}}</li>
            <li><strong>Lingua:</strong>{{elm.original_language}}</li>
            <li><strong>Voto:</strong> {{elm.vote_average}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'MovieCard',
    props:['info'],
}
</script>

<style lang="scss" scoped>

</style>