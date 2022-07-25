<template>
  <div id="app">
    <Header @search=GetApiRequest />
    <Main
      :movies="SearchedMovies"
      :tvShows="searchedTvShow"
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
    }
  },
  methods:{
    
    GetApiRequest(name){
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=66df3909187524734aebd03e217fd826&query='+ name)
        .then((result)=>{
          this.SearchedMovies=result.data.results;
        
          for (let i = 0; i < this.SearchedMovies.length; i++) {
            this.SearchedMovies[i].cast=[];
            axios.get("https://api.themoviedb.org/3/movie/"+ this.SearchedMovies[i].id + "/credits?api_key=66df3909187524734aebd03e217fd826")
            .then((risultato)=>{
                for (let a = 0; a < 5; a++) {
                  this.SearchedMovies[i].cast.push(risultato.data.cast[a].name);
                  
                }
            });
          }
        });

      axios.get('https://api.themoviedb.org/3/search/tv?api_key=66df3909187524734aebd03e217fd826&query='+ name)
        .then((result)=>{
          this.searchedTvShow=result.data.results;
          
          for (let k= 0; k < this.SearchedMovies.length; k++) {
            this.searchedTvShow[k].cast=[];
            axios.get("https://api.themoviedb.org/3/tv/"+ this.searchedTvShow[k].id + "/credits?api_key=66df3909187524734aebd03e217fd826")
            .then((risultato)=>{
                for (let j = 0; j < 5; j++) {
                  this.searchedTvShow[k].cast.push(risultato.data.cast[j].name);
                  
                }
            });
          }
      });
    },
    
  },
  
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";
body{
  background-color: rgb(7, 7, 7);
}
</style>
