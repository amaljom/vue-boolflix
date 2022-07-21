<template>
    <div >
        <div class="row col-10 mx-card-container">
            <SingleMovieCard v-for="(movie, index) in movies"
            :key="index"
            :movie="movie" />
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
            movies:{
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