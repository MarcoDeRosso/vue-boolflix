<template>
  <div class="container" id="app">
    <Header @search="searchFilm"/>
    <Main  :list="list"/>
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue'
import Main from './components/Main.vue'


export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return{
      list:[],
      inputSearch: '',
      apiPopular:'https://api.themoviedb.org/3/movie/popular?api_key=f9f2d73c3435d93318563278430d4304'
    }
  },
  created(){
    this.createApi(this.apiPopular)
  },
  methods: {
     createApi(api){
       axios.get(api).then((result)=>{
          this.list = result.data.results;
       })

     },
      searchFilm(searchString) {
      this.inputSearch = searchString.trim()
      if(this.inputSearch.length === 0) {
        this.createApi(this.apiPopular)
        return;
      } 
      let api='https://api.themoviedb.org/3/search/multi?api_key=f9f2d73c3435d93318563278430d4304&query=';
      api += this.inputSearch;
      this.createApi(api);
      
    }
  }
}
</script>

<style lang="scss">
@import "./style/app.scss"
</style>