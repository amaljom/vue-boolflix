<template>
    <div class="bg-header d-flex justify-content-between align-items-center">
      <div>
        <img class="logo" src="https://www.giornaleadige.it/wp-content/uploads/2021/09/Netflix-Logo.png" alt="NON TROVATO">
      </div>

      <div class="search-div">
          <input class=" input text-white" type="text" placeholder="cerca un film" v-model="movieToSearch" @keyup.enter="$emit('search',movieToSearch)">
          <div class="button" >
              <i class="fa-solid fa-magnifying-glass text-white m-1" @click="$emit('search',movieToSearch)" ></i>
          </div>
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

<style lang='scss' scoped>


.button{
  padding: 5px;
  background-color: #2f3640;
  border-radius: 40px;
  border: solid 2px;
  transition-duration: .7s;
  &:hover{
    cursor: pointer;
  }
}
.input{
  border: none;
  background: none;
  outline: none;
  width: 0px;
  transition-duration: .7s;
}
.search-div{
  display: flex;
  background-color: rgb(48, 48, 48);
  padding: 8px;
  margin-right: 10px;
  border-radius: 40px;
    &:hover .input{
      width: 200px;
    }
    &:hover .button{
      background-color: #b60000;
    }

}
.bg-header{
  background-color: rgb(12, 12, 12);
}
.logo{
  width: 100px;
  margin: 10px;
}
</style>


