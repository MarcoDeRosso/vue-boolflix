<template>
    <div>
        <div class="container-card position-relative">
            <img class="poster" :src="posterImg(poster_path)" alt="">
            <div class="info-container d-flex flex-column align-items-center position-absolute bottom-0 start-50 translate-middle-x">
                <h1>{{title}}{{name}}</h1>
                <div class="line"></div>
                <h3>Titolo Originale: {{original_title}}{{original_name}}</h3>
                <div>Lingua: <img class="flag" :src="flagImg(original_language)" alt="flag"></div>
                <div class="star"><i v-for="n in 5" :key="n" class="fa-star m-2" :class="n <= voteRounded ? 'fas': 'far'"></i></div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:'Card',
    data() {
        return {
            voteRounded: Math.round(this.vote_average /2)
        }
    },
    props:{
        original_title:String,
        name:String,
        original_name:String,
        title:String,
        original_language:String,
        vote_average:Number,
        poster_path:String,
    },
    methods:{
        flagImg(flag){
            if(!this.original_language){
                return require("../assets/white.png")
            }
            return require ("../assets/"+flag+".png");
        },
        posterImg(img){
            if(this.poster_path == null){
                return require("../assets/netflix-1.jpg")
            }
            return "http://image.tmdb.org/t/p/w500/"+img;
        },
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
        .poster{
            height: 500px;
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
            .line{
                border: 1px solid $white-text;
                width: 20%;
            }
            .flag{
                width: 30px;
            }
            .star{
                i{
                    color: $gold;
                }
            }
        }
    }

</style>