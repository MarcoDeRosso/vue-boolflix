<template>
    <main>
        <h1>ORIGINAL NETFLIX</h1>
        <div v-if="listSerie.length === 0 && listFilm.length === 0" class="row">
            <h1>Popolar</h1>
            <Card class="col-3 my-3" v-for="film in listPopolar" :key="film.id" 
            :original_title="film.original_title"
            :title="film.title"
            :name="film.name"
            :original_name="film.original_name"
            :original_language="film.original_language"
            :vote_average="film.vote_average" 
            :poster_path="film.poster_path"
            />
        </div>
        <div v-else>
            <div  class="row">
                <h1>TV Series</h1>
                <div class="col">
                    <div v-if="indexSerie > 0" class="arrow d-flex flex-row-reverse align-content-center align-items-center" @click="prev">
                        <i class="fas fa-arrow-circle-left"></i>
                    </div>
                </div>
                <Card class="col-card my-3" v-for="film in newListSeire" :key="film.id" 
                :original_title="film.original_title"
                :title="film.title"
                :name="film.name"
                :original_name="film.original_name"
                :original_language="film.original_language"
                :vote_average="film.vote_average" 
                :poster_path="film.poster_path"
                />
                <div class="col">
                    <div class="arrow d-flex align-content-center align-items-center" @click="next">
                        <i class="fas fa-arrow-circle-right"></i>
                    </div>
                </div>
            </div>
            <div class="row">
                <h1>Movie</h1>
                <div class="col">
                    <div v-if="indexFilm > 0" class="arrow d-flex flex-row-reverse align-content-center align-items-center" @click="prevFilm">
                        <i class="fas fa-arrow-circle-left"></i>
                    </div>
                </div>
                <Card class="col-card my-3" v-for="film in newListFilm" :key="film.id" 
                :original_title="film.original_title"
                :title="film.title"
                :name="film.name"
                :original_name="film.original_name"
                :original_language="film.original_language"
                :vote_average="film.vote_average" 
                :poster_path="film.poster_path"
                />
                <div class="col">
                    <div class="arrow d-flex align-content-center align-items-center" @click="nextFilm">
                        <i class="fas fa-arrow-circle-right"></i>
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>

<script>
import Card from "./Card.vue"
export default {
    name:'Main',
    components:{
        Card
    },
    props:{
        listPopolar:Array,
        listFilm:Array,
        listSerie:Array,
    },
    data(){
        return{
            indexFilm:0,
            indexSerie:0
        }
    },
    computed:{
        newListFilm(){
            return this.listFilm.slice(this.indexFilm, (this.indexFilm + 4))
        },
        newListSeire(){
            return this.listSerie.slice(this.indexSerie, (this.indexSerie + 4))
        },
    },
    methods:{
        next(){
            if (this.indexSerie >= (this.listSerie.length - 4)) {
                this.indexSerie = 0;
            } else {
                this.indexSerie +=4;
            }
        },
        prev(){
            if (this.indexSerie === 0) {
                this.indexSerie = 0;
            } else {
                this.indexSerie -=4;
            }
        },
        nextFilm(){
            if (this.indexFilm >= (this.listFilm.length - 4)) {
                this.indexFilm = 0;
            } else {
                this.indexFilm +=4;
            }
        },
        prevFilm(){
            if (this.indexFilm === 0) {
                this.indexFilm = 0;
            } else {
                this.indexFilm -=4;
            }
        }
    }
}
</script>

<style lang="scss" scoped>
@import "../style/colors.scss";
    main{
        .col-card{
            width: calc(100% / 4 - 38px);
        }
        h1{
            color: $white-text;
        }
        .arrow {
            width: 100%;
            height: 100%;
            font-size: 50px;
            color: $white-text;
            &:hover i{
                cursor: pointer;
            }
        }
    }

</style>