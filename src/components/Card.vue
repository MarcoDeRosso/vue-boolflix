<template>
    <div>
        <img src="https://image.tmdb.org/t/p/w342/hQq8xZe5uLjFzSBt4LanNP7SQjl.jpg" alt="">
    </div>
</template>

<script>
export default {
    name:'Card',
    props:{
        poster_path:String
    },
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