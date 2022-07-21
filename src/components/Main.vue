<template>
    <div >
        <div class="row col-10 mx-card-container">
            <SingleMovieCard v-for="(searchedMovie, index) in SearchedMovies"
            :key="index"
            :SearchedMovies=SearchedMovies />
        </div>
        
    </div>
</template>

<script>
    import SingleMovieCard from './SingleMovieCard'
    
    export default {
        components:{
            SingleMovieCard
        },
        props:{
            'SearchedMovies':{
                type: Array
            }
        }
    }
</script>

<style scoped lang='scss'>
.mx-card-container{
    margin: 0 auto;
    justify-content: center;
}
</style>