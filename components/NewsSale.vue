<template>
    <div class="sale relative">
        <img :src="sale.cover" alt="">
    </div>
</template>

<script>
export default {
    name: 'Expres24NuxtNewsSale',
    props : ["sale"],
    data() {
        return {
           
        };
    },

    mounted() {
        
        
    },

    methods: {
        
    },
};
</script>

<style scoped>
    .sale{
        width: 300px ;
        height: 200px;
        margin: 50px 15px;
    }
    img{
        width: 100%;
        height: auto;
        object-fit:cover;
        border-radius: 16px;
        transition: all 0.3s ease;
    }
    img:hover{
        transform: scale(1.1);
    }
</style>