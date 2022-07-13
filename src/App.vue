<template>
  <div id="app">
    <!-- Header -->
    <header>
      <HeaderComp @apiShow="apiShow" />
    </header>

    <main>
      <MainComp :getArrayMovie="movieArray" :getArrayTvShow="tvShowArray"/>
    </main>
  </div>
</template>

<script>
import MainComp from './components/MainComp.vue'
import HeaderComp from './components/HeaderComp.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    MainComp,
    HeaderComp
  },

  data() {
    return {
      getResult: '',
      urlMovie: 'https://api.themoviedb.org/3/search/movie?api_key=1a9d4ad303208935b21b8e064d453ab7&language=it-IT&query=',
      urlTvShow: 'https://api.themoviedb.org/3/search/tv?api_key=6cf9d861dc5d32d698a74fadc1c4a561&language=en-US&page=1&include_adult=false&query=',
      movieArray: [],
      tvShowArray: []
    }
  },

  methods: {
    // Show e' il parametro dell-input che ho passato dall'header
    apiShow(show){
      // Unisco l'url fisso(film) con l'input dell'utente
      this.getResult = `${this.urlMovie}${show}`
        // Richiesta lista di film 
        axios.get(this.getResult).then((response) => {
        this.movieArray = response.data.results;
      });
      
      // Unisco l'url fisso(tv Show) con l'input dell'utente
      this.getResult = `${this.urlTvShow}${show}`
        // Richiesta lista di tv show 
        axios.get(this.getResult).then((response) => {
        this.tvShowArray = response.data.results;
      });
      
    }
  },

  created() {
    this.apiShow()
  }
}
</script>

<style lang="scss">
@import './style/common.scss';
@import './style/variables.scss';

</style>
