<template>
    <div class="movie-card">
            <div><strong>Titolo:</strong>{{info.title}}</div>
            <div><strong>Titolo orginale:</strong>{{info.original_title}}</div>
            <div><strong>lingua:</strong>{{info.original_language}}</div>
            <div><strong>Voto:</strong>{{info.vote_average}}</div>
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