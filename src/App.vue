<template>
  <div class="container" id="app">
    <Header @search="searchFilm"/>
    <Main  :list="filteredFilms"/>
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
      api:'https://api.themoviedb.org/3/search/movie?api_key=f9f2d73c3435d93318563278430d4304&query=ritorno+al+futuro'
    }
  },
  created(){
    this.createApi(this.api)
  },
  computed: {
    filteredFilms() {
      // elements è una lista di elementi in cui deve cercare "search"
      function searchIn(search, elements) {
        let exists = false;
        elements.forEach((element) => {
          if(element.toLowerCase().includes(search.toLowerCase())) {
            exists = true;
          }
        });
        return exists;
      }
      if(this.inputSearch.length === 0) {
        return this.list
      } 
      return this.list.filter((element) => {
        return searchIn(this.inputSearch, [element.original_title, element.title,])
      })
    }
  },
   methods: {
     createApi(api){
       axios.get(api).then((result)=>{
          this.list = result.data.results;
          this.searchFilm('')
       })

     },
      searchFilm(searchString) {
      this.inputSearch = searchString.trim()
      let api='https://api.themoviedb.org/3/search/movie?api_key=f9f2d73c3435d93318563278430d4304&query='
      api += this.inputSearch
      this.createApi(api)
    }
  }
}
</script>

<style lang="scss">
@import "./style/app.scss"
</style>