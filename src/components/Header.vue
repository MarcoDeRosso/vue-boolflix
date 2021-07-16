<template>
    <header class="d-flex justify-content-between align-items-center p-3">
        <nav class="left-nav d-flex align-items-center">
            <img src="../assets/logo.png" alt="logo">
            <ul class="d-flex">
                <li><a href="#">Home</a> </li>
                <li><a href="#">Serie TV</a></li>
                <li><a href="#">Film</a></li>
                <li><a href="#">Originali</a></li>
                <li><a href="#">Aggiunti di recente</a></li>
                <li><a href="#">La mia lista</a></li>
            </ul>
        </nav>
        <nav class="right-nav">
            <div class="input-group ">
                <input @keyup.enter="$emit('search', searchString)" type="text" class="form-control" placeholder="Search" v-model="searchString">
                <button @click="$emit('search', searchString)" class="btn btn-outline-secondary" type="button" id="button-addon2">Search</button>
            </div>
        </nav>
       
    </header>
</template>

<script>
export default {
    name:'Header',
        data() {
        return {
            searchString: ''
        }
    },
        props:{

    }
}
</script>

<style lang="scss" scoped>
@import "../style/colors.scss";
header{
    .left-nav{
        img{
            width: 100px;
        }
        ul{
            li{
                margin: 0 12px
            }
        }
    }
    .right-nav{
        .input-group{
            .btn{
                color: $white-text;
            }
        }
    }
}

</style>