<template>
<div>
    <p v-for="(element,index) in elemento" :key="index" > {{ element }} </p>
    
</div>
    
</template>

<script>
export default {
    props:['elemento']
}
</script>

<style>

</style>