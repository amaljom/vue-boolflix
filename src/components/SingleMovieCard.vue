<template>
    <div class="mx-card col-2 bg-danger text-center m-3 p-4">
        <div v-if="movie.poster_path!=null">
            <img :src="(`https://image.tmdb.org/t/p/w154${movie.poster_path}`)" alt="">
        </div>
        <h3>{{movie.title}}</h3>
        <h3>{{movie.original_title}}</h3>
        <div v-if="languageFinder(movie.original_language)!=0" class="img-container mx-card">
             <img class="w-100" :src="languageFinder(movie.original_language)" alt="">
        </div>
        <p v-else>{{ movie.original_language }}</p>
        <p>{{movie.vote_average}}</p>
        
    </div>
</template>

<script>
export default {
    props:['movie'],

    methods:{
        languageFinder(language){
            switch (language) {
                case 'en':
                    return 'https://upload.wikimedia.org/wikipedia/en/thumb/a/ae/Flag_of_the_United_Kingdom.svg/1200px-Flag_of_the_United_Kingdom.svg.png'
                    break;
                
                case 'it':
                    return 'https://upload.wikimedia.org/wikipedia/en/thumb/0/03/Flag_of_Italy.svg/255px-Flag_of_Italy.svg.png'
                    break;
                case 'es':
                    return 'https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Flag_of_Spain.svg/1280px-Flag_of_Spain.svg.png'
                    break;
                case 'de':
                    return 'https://upload.wikimedia.org/wikipedia/commons/d/d8/Flagge_Deutschland.jpg'
                    break;
                case 'fr':
                    return 'https://upload.wikimedia.org/wikipedia/en/thumb/c/c3/Flag_of_France.svg/250px-Flag_of_France.svg.png'
                    break;
                default:
                    return 0
                    break;
            }
        }
    }
}

</script>

<style scoped lang='scss'>
.mx-card{
    margin: 0 auto;
}
.img-container{
    width: 40px;
}
</style>