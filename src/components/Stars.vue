<template>
    <div class="d-flex justify-content-center mt-3">
        <i v-for="n in 5" class="fa-solid fa-star" :class="getClass(n, vote)" :key="n"></i>
    </div>
</template>

<script>
export default {
    props:['vote'],
    methods:{
        getClass(n, vote){
            if (n<=vote) {
                return 'text-warning'
        }
        
            
        }
    }
}
</script>

<style>

</style>