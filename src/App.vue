<template>
  <div id="app">
    <Header @search=GetApiRequest />
    <Main @searchingCast=CastById
      :movies="SearchedMovies"
      :tvShows="searchedTvShow"
      :casts="searchedMovieCast"
    />
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
      SearchedMovies:[],
      searchedTvShow:[],
      searchedMovieCast:[]
    }
  },
  methods:{
    GetApiRequest(name){
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=66df3909187524734aebd03e217fd826&query='+ name)
        .then((result)=>{
          this.SearchedMovies=result.data.results;
      });
      axios.get('https://api.themoviedb.org/3/search/tv?api_key=66df3909187524734aebd03e217fd826&query='+ name)
        .then((result)=>{
          this.searchedTvShow=result.data.results;
      });
    },
    CastById(id){
      axios.get(`https://api.themoviedb.org/3/movie/${id}/credits?api_key=66df3909187524734aebd03e217fd826`)
        .then((result)=>{
          for (let i = 0; i < 5; i++) {
            this.searchedMovieCast[i]=result.data.cast[i]
            console.log(this.searchedMovieCast);
          }
      });
    }
  }
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";
body{
  background-color: rgb(7, 7, 7);
}
</style>
