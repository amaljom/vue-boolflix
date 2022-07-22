<template>
    <div class="bg-header d-flex justify-content-between align-items-center">
      <div>
        <img class="logo" src="https://www.giornaleadige.it/wp-content/uploads/2021/09/Netflix-Logo.png" alt="NON TROVATO">
      </div>
      <div>
        <input class="p-2 m-2 " type="text" placeholder="cerca un film" v-model="movieToSearch">
        <i class="fa-solid fa-magnifying-glass text-light me-3 "  @click="$emit('search',movieToSearch)"></i>  
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
.bg-header{
  background-color: rgb(12, 12, 12);
}
.logo{
  width: 100px;
  margin: 10px;
}
</style>


