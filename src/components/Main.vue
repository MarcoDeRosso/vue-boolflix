<template>
    <main>
        <h1>ORIGINAL NETFLIX</h1>
        <div class="row">
            <Card class="col" v-for="film in listTry.results" :key="film.id" 
            :original_title="film.original_title"
            :title="film.title"
            :original_language="film.original_language"
            :vote_average="film.vote_average" />
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
        listTry:Object
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