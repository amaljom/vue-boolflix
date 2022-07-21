<template>
  <div>
    <input type="text" placeholder="cerca un film" v-model="movieToSearch">
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