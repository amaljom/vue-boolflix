<template>
    <div class="bg-dark d-flex justify-content-between align-items-center">
      <div>
        <img class="logo" src="https://www.giornaleadige.it/wp-content/uploads/2021/09/Netflix-Logo.png" alt="NON TROVATO">
      </div>
      <div>
        <input class="p-2 m-2 " type="text" placeholder="cerca un film" v-model="movieToSearch">
      <div class="btn btn-primary" @click="$emit('search',movieToSearch)"> submit </div>   
    </div>
  </div>
  
</template>

<script>
export default {
    data:function(){
        return{
            movieToSearch:'' 
        }
    },
}
</script>

<style>
.logo{
  width: 100px;
  margin: 10px;
}
</style>


// 66df3909187524734aebd03e217fd826 api key (me lo segno qua per comodità al momentp)
// https://api.themoviedb.org/3/search/movie?api_key=66df3909187524734aebd03e217fd826&query=dark