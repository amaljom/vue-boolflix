<template>
  <div id="app">
    <Header @search=GetApiRequest />
    <Main :movies="SearchedMovies" />
  </div>
</template>

<script>

import Header from './components/Header'
import Main from './components/Main'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data: function(){
    return{
      SearchedMovies:[]
    }
  },
  methods:{
    GetApiRequest(name){
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=66df3909187524734aebd03e217fd826&query='+ name)
        .then((result)=>{
          this.SearchedMovies=result.data.results;
      });
    }
  }
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";
</style>
