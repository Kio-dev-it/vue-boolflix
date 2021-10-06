<template>
    <header>
        <form>
            <input type="text" placeholder="Cerca il film" v-model="searchText">
            <button @click.prevent="$emit('searchMovie', searchText)">Cerca</button>
        </form>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data(){
        return{
            searchText:""
        }
    }
}
</script>

<style lang="scss" scoped>

</style>