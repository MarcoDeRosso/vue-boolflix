<template>
    <div>
        <carousel :autoplay="true" :centerMode="true" :loop="true" :perPage="4">
            <slide v-for="img in listPopolar" :key="img.id">
                <div class="container-card" :style="'background-image:url('+posterImg(img.poster_path)+')'"></div>
                <!-- <img :src="`http://image.tmdb.org/t/p/w500/${img.poster_path}`" alt=""> -->
            </slide>
        </carousel>
       
    </div>
</template>

<script>
import { Carousel, Slide } from 'vue-carousel';
export default {
    name:'Slider',
    components: {
        Carousel,
        Slide
     },
        data() {
        return {
            imgIndex: 0,
            imgList:[
                
            ]
        }
    },
    props:{
        listPopolar:Array,
    },
    methods:{
        posterImg(img){
            return "http://image.tmdb.org/t/p/w500/"+img;
        },
    }
}
</script>

<style lang="scss" scoped>
@import "../style/colors.scss";
    .container-card{
        width: 100%;
        height: 500px;
        background-size: cover;
        background-position: center;
    }
</style>