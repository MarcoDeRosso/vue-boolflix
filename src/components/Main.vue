<template>
    <main>
        <h1>ORIGINAL NETFLIX</h1>
        <div class="row">
            <Card class="col-4 my-4" v-for="film in list" :key="film.id" 
            :original_title="film.original_title"
            :title="film.title"
            :name="film.name"
            :original_name="film.original_name"
            :original_language="film.original_language"
            :vote_average="film.vote_average" 
            :poster_path="film.poster_path"
            />
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
        list:Array
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