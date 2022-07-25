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
      searchedMovieCast:''
      // castMembers:{
      //   name1:'',
      //   name2:'',
      //   name3:'',
      //   name4:'',
      //   name5:''          
      // }
    }
  },
  methods:{
    
    GetApiRequest(name){
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=66df3909187524734aebd03e217fd826&query='+ name)
        .then((result)=>{
          this.SearchedMovies=result.data.results;
        });
          for (let i = 0; i < this.SearchedMovies.length; i++) {
            this.SearchedMovies[i].cast=[];
            this.searchedMovieCast=this.SearchedMovies[i].id;
            console.log(this.searchedMovieCast);
              // axios.get("https://api.themoviedb.org/3/movie/"+ castToSearc + "/credits?api_key=66df3909187524734aebd03e217fd826")
              // .then((result)=>{
              
            // });
          }

      axios.get('https://api.themoviedb.org/3/search/tv?api_key=66df3909187524734aebd03e217fd826&query='+ name)
        .then((result)=>{
          this.searchedTvShow=result.data.results;
      });
    },
    
      // axios.get(`https://api.themoviedb.org/3/movie/${id}/credits?api_key=66df3909187524734aebd03e217fd826`)
      //   .then((result)=>{
      //       for (let i = 0; i < array.length; i++) {
      //         const element = array[i];
              
      //       }
              // this.castMembers={
              //   name1:result.data.cast[0],
              //   name2:result.data.cast[1],
              //   name3:result.data.cast[2],
              //   name4:result.data.cast[3],
              //   name5:result.data.cast[4]
              // };
              //  this.searchedMovieCast.push(this.castMembers);
            
      // });
    },
  // }
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";
body{
  background-color: rgb(7, 7, 7);
}
</style>
