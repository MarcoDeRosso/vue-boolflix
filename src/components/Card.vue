<template>
    <div>
        <div class="container-card position-relative">
            <img :src="`http://image.tmdb.org/t/p/w500/${poster_path}`" alt="">
            <div class="info-container position-absolute bottom-0 start-50 translate-middle-x">
                <h2>{{title}}</h2>
                <h3>Titolo Originale: {{original_title}}</h3>
                <h4>Lingua: {{original_language}}</h4>
                <img class="flag" :src="flagImg(original_language)" alt="flag">
                <h3>Voto: {{vote_average}}</h3>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:'Card',
    props:{
        original_title:String,
        title:String,
        original_language:String,
        vote_average:Number,
        poster_path:String,
    },
    methods:{
        flagImg(flag){
            return require ("../assets/"+flag+".png");
        }
    }
}
</script>

<style lang="scss" scoped>
@import "../style/colors.scss";
    .container-card{
        width: 100%;
        max-height: 500px;
        img{
            width: 100%;
            max-height: 500px;
        }
        &:hover .info-container{
            opacity: 1;
        }
        .info-container{
            color: $white-text;
            width: 100%;
            text-align: center;
            background: rgba($color: #000000, $alpha: 0.6);
            opacity: 0;
        }
        .flag{
            width: 30px;
        }
    }

</style>