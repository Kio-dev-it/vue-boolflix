<template>
  <div id="app">
    <Header @searchMovie="searching"/>
    <Movies :infoSearch="searchMovie"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Movies from './components/Movies.vue'


export default {
  name: 'App',
  components: {
    Header,
    Movies
  },
  data(){
    return{
      searchMovie:""
    }
  },
  methods:{
    searching(text){
      this.searchMovie = text;
    }
  }
}
</script>

<style lang="scss">

</style>
