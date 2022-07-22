<template>
    <div>
        <div class="row col-11 mx-card-container">
            <SingleMovieCard v-for="movie in movies"
            :key="movie.id"
            :movie="movie" />
        </div>
        <div class="row col-10 mx-card-container">
            <SingleShowCard v-for="tvShow in tvShows"
            :key="tvShow.id"
            :tvShow="tvShow" />
        </div>
    </div>
</template>

<script>
    import SingleMovieCard from './SingleMovieCard'
    import SingleShowCard from './SingleShowCard'
    
    export default {
        components:{
            SingleMovieCard,
            SingleShowCard
        },
        props:{
            movies:{
                type: Array,
                required:true
            },
            tvShows:{
                type: Array,
                required:true
            },
            
        }
    }
        
    
</script>

<style scoped lang='scss'>
.mx-card-container{
    margin: 0 auto;
    justify-content: center;
}
</style>