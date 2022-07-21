<template>
    <div class="mx-card col-2 bg-danger text-center m-3 p-4">
        <h2>{{movie.title}}</h2>
        <h2>{{movie.original_title}}</h2>
        <h4>{{movie.original_language}}</h4>
        <h4>{{movie.vote_average}}</h4>
    </div>
</template>

<script>
export default {
     props:['movie']
}
</script>

<style scoped lang='scss'>
.mx-card{
    margin: 0 auto;
}
</style>