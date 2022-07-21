<template>
    <div class="mx-card col-2 bg-danger text-center m-3 p-4">
        <h2>{{ SearchedMovies.title }}</h2>
        <h2>titolo originale</h2>
        <h4>lingua</h4>
        <h4>voto</h4>
    </div>
</template>

<script>
export default {
     props:['SearchedMovies']
}
</script>

<style scoped lang='scss'>
.mx-card{
    margin: 0 auto;
}
</style>