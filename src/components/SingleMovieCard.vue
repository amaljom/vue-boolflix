<template>
    <div class="mx-card bg-card text-center m-3 g-0">
        <div v-if="movie.poster_path!=null">
            <img class="poster" :src="(`https://image.tmdb.org/t/p/w342${movie.poster_path}`)" alt="">
        </div>
        <div class="text-white center-content" :class="getClassIfImgNull(movie.poster_path)">
            <h3>Titolo: {{movie.title}}</h3>
            <h3 v-if="(movie.title != movie.original_title )">Titolo originale: {{movie.original_title}}</h3>
            <div v-if="languageFinder(movie.original_language)!=0" class="img-container mx-auto">
                <img class="w-100" :src="languageFinder(movie.original_language)" alt="">
            </div>
            <p v-else>{{ movie.original_language }}</p>
            <Stars
            :vote="voteToFive(movie.vote_average)"/>
            <div>
                <p v-for="(element, index) in casts" :key="index">{{element.name}}</p>
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
    props:['movie', 'casts'],

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
        },
        getClassIfImgNull(result){
            if (result!=null) {
                return 'info-div';
            }
        },
        getCastMovie(){
            this.$emit('GetCast', this.movie.id);
        }
    },
    created(){
        this.getCastMovie()
    }
}

</script>

<style scoped lang='scss'>
.center-content{
    position: relative;
    top: 80px;
}
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
.bg-card{
    background-color: rgb(15, 15, 15);
}
</style>