<template>
    <main>
        <h1>ORIGINAL NETFLIX</h1>
        <div class="row">
            <Card  v-for="film in listTry" :key="film.id" :poster_path="film.poster_path" class="col"/>
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