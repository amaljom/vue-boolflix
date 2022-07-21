<template>
  <div id="app">
    <Header @search=GetApiRequest />
    <Main/>
  </div>
</template>

<script>

import Header from './components/Header'
import Main from './components/Main'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data: function(){
    return{
      name:''
    }
  },
  methods:{
    GetApiRequest(nome){
      console.log(nome);
    }
  }
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";
</style>
