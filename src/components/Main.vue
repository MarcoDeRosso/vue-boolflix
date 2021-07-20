<template>
    <main>
        <h1>ORIGINAL NETFLIX</h1>
        <div v-if="listSerie.length === 0 && listFilm.length === 0" class="row">
            <h1>Popolar</h1>
            <Card class="col-3 my-4" v-for="film in listPopolar" :key="film.id" 
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
                <Card class="col-3 my-4" v-for="film in listSerie" :key="film.id" 
                :original_title="film.original_title"
                :title="film.title"
                :name="film.name"
                :original_name="film.original_name"
                :original_language="film.original_language"
                :vote_average="film.vote_average" 
                :poster_path="film.poster_path"
                />
            </div>
            <div class="row">
                <h1>Movie</h1>
                <Card class="col-3 my-4" v-for="film in listFilm" :key="film.id" 
                :original_title="film.original_title"
                :title="film.title"
                :name="film.name"
                :original_name="film.original_name"
                :original_language="film.original_language"
                :vote_average="film.vote_average" 
                :poster_path="film.poster_path"
                />
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
    }
}
</script>

<style lang="scss" scoped>
@import "../style/colors.scss";
    main{
        h1{
            color: $white-text;
        }
    }

</style>