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
        <nav class="right-nav d-flex align-items-center">
            <div class="input-group ">
                <input v-if="flag" @keyup="$emit('search', searchString)" type="text" class="form-control" placeholder="Search" v-model="searchString">
                <button @click="serchShow" class="btn btn-outline-secondary" type="button" id="button-addon2"><i class="fas fa-search"></i></button>
            </div>
            <ul class="d-flex">
                <li><a href="#">BAMBINI</a></li>
                <li><a href="#"><i class="fas fa-bell"></i></a></li>
            </ul>
        </nav>
       
    </header>
</template>

<script>
export default {
    name:'Header',
        data() {
        return {
            searchString: '',
            flag:false,
        }
    },
    methods:{
        serchShow(){
            if (this.flag === false){
                this.flag=true;
            } else{
                this.flag=false;
            }
        }
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
            padding-top: 12px;
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
        ul{
            padding-top: 12px;
            li{
                margin: 0 12px
            }
        }
    }
}

</style>