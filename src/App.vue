<template>
  <div id="app">
    <!-- Header -->
    <header>
      <HeaderComp @apiShow="apiShow" />
    </header>

    <main>
      <MainComp :getArray="movieArray"/>
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
      userChoose: '',
      urlMovie: 'https://api.themoviedb.org/3/search/movie?api_key=1a9d4ad303208935b21b8e064d453ab7&language=it-IT&query=',
      movieArray: [],
    }
  },

  methods: {
    // Show e' il parametro dell-input che ho passato dall'header
    apiShow(show){
      // Richiedo lista di show in base alla ricerca dell'utente
      this.getResult = `${this.urlMovie}${show}`
      console.log(this.getResult);
      
        axios.get(this.getResult).then((response) => {
        this.movieArray = response.data.results
      });
       console.log('app', this.userChoose);
    }
  }
}
</script>

<style lang="scss">
@import './style/common.scss';
@import './style/variables.scss';

</style>
