<template>
    <header class="d-flex justify-content-between align-items-center py-3">
        <nav class="left-nav">
            <ul class="d-flex justify-content-between align-items-center">
                <li><img src="../assets/logo.png" alt="logo"></li>
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
                <input v-if="flag" @keyup.enter="$emit('search', searchString)" type="text" class="form-control" placeholder="Press Enter for Search" v-model="searchString">
                <button @click="serchShow" class="btn btn-outline-secondary" type="button" id="button-addon2"><i class="fas fa-search"></i></button>
            </div>
            <ul class="d-flex align-items-center">
                <li><a href="#">BAMBINI</a></li>
                <li><a href="#"><i class="fas fa-bell"></i></a></li>
                <li><img class="avatar" src="../assets/Netflix-avatar.png" alt="avatar"></li>
                <li><a href="#"><i class="fas fa-sort-down"></i></a></li>
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
                this.searchString= "";
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
            padding-left: 0;
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
            padding-left: 0;
            padding-top: 12px;
            li{
                margin: 0 12px
            }
            .avatar{
                width: 30px;
            }
            li:last-child{
                margin-left: 0;
            }
        }
    }
}

</style>