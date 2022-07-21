<template>
  <div class="bg-success">
    <input class="p-2 m-2 " type="text" placeholder="cerca un film" v-model="movieToSearch">
    <div class="btn btn-primary"> submit </div>   
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

</style>


// 66df3909187524734aebd03e217fd826 api key (me lo segno qua per comodità al momentp)
// https://api.themoviedb.org/3/search/movie?api_key=66df3909187524734aebd03e217fd826&query=dark