<template>
  <div class="container" id="app">
    <Header @search="[searchFilm($event),searchSerie($event)]"/>
    <Main :listFilm="listFilm" :listSerie="listSerie"  :listPopolar="listPopolar"/>
  </div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue'
import Main from '@/components/Main.vue'


export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return{
      listPopolar:[],
      listFilm:[],
      listSerie:[],
      inputSearch: '',
      apiPopular:'https://api.themoviedb.org/3/movie/popular?api_key=f9f2d73c3435d93318563278430d4304'
    }
  },
  created(){
      axios.get(this.apiPopular).then((result)=>{
        this.listPopolar = result.data.results;
      })
  },
  methods: {
    searchFilm(searchString) {
      this.inputSearch = searchString.trim()
      if(this.inputSearch.length === 0) {
        return this.listFilm = [];
      } 
      let api='https://api.themoviedb.org/3/search/movie?api_key=f9f2d73c3435d93318563278430d4304&query=';
      api += this.inputSearch;
        axios.get(api).then((result)=>{
          this.listFilm = result.data.results;
        })
    },
    searchSerie(searchString) {
      this.inputSearch = searchString.trim()
      if(this.inputSearch.length === 0) {
        return this.listSerie = [];
      } 
      let api='https://api.themoviedb.org/3/search/tv?api_key=f9f2d73c3435d93318563278430d4304&query=';
      api += this.inputSearch;
        axios.get(api).then((result)=>{
          this.listSerie = result.data.results;
        })
    },
    
  }
}
</script>

<style lang="scss">
@import "./style/app.scss"
</style>