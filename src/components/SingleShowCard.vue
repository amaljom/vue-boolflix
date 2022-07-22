<template>
    <div class="mx-card bg-danger text-center m-3 g-0">
        <div v-if="tvShow.poster_path!=null">
            <img class="poster" :src="(`https://image.tmdb.org/t/p/w154${tvShow.poster_path}`)" alt="">
            <div class="text-white info-div">
                <h3>{{tvShow.name}}</h3>
                <h3>{{tvShow.original_name}}</h3>
                <div v-if="languageFinder(tvShow.original_language)!=0" class="img-container mx-card">
                    <img class="w-100" :src="languageFinder(tvShow.original_language)" alt="">
                </div>
                <p v-else>{{ tvShow.original_language }}</p>
                <Stars
                :vote="voteToFive(tvShow.vote_average)"/>
            </div>
        </div>
    </div>
</template>

<script>
import Stars from './Stars'
export default {
    components:{
        Stars
    },
    props:['tvShow'],
    
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
        },
        voteToFive(votevalue){
            return Math.ceil(votevalue / 2);
        }
    }
    

}

</script>

<style scoped lang='scss'>
.mx-card{
    margin: 0 auto;
    width: 342px;
    height: 490px;
    &:hover .poster{
        display: none;
    }
    &:hover .info-div{
        display: inline;
    }
}
.poster{
    width: 342px;
    height: 490px;
    object-fit: cover;
    
}
.img-container{
    width: 40px;
}
.info-div{
    display: none;
}
</style>