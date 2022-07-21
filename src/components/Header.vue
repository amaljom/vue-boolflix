<template>
  <div class="bg-success">
    <input class="p-2 m-2 " type="text" placeholder="cerca un film" v-model="movieToSearch">
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