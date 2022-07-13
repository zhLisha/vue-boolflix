<template>
  <div >
    <ul>
      <li  v-for="item, index in getArray" :key="index">
        <img :src="'https://image.tmdb.org/t/p/original/' + item.poster_path" :alt="item.title">
        <div class="title">
          <span>Titolo: </span>
          {{item.title}}
        </div>
        <div class="original-title">
          <span>Titotlo Originale: </span>
          {{item.original_title}}
        </div>
        <div class="language">
          <span>Lingua: </span>
          {{item.spoken_languages}}
        </div>
        <div class="rated">
          <span>Voto: </span>
          {{item.vote_average}}
        </div>
      </li>
    </ul>
  </div>
</template>

<script>


export default {
  name: 'MainComp',
  props: {
    getArray: Array
  },

  // data() {
  //   return {
  //     // urlMovie: 'https://api.themoviedb.org/3/search/movie?api_key=1a9d4ad303208935b21b8e064d453ab7&language=it-IT&query=',
  //     urlMovie: 'https://api.themoviedb.org/3/movie/550?api_key=6cf9d861dc5d32d698a74fadc1c4a561',
  //     movieArray: [],
  //     getResult: '',
  //   }
  // },

  // methods: {
  //   getApi() {
  //     // Richiedo lista di show in base alla ricerca dell'utente
  //     this.getResult = `${this.urlMovie}${this.getUserChoose}`
  //     console.log(this.getResult);
      
  //       axios.get(this.getResult).then((response) => {
  //         const array = response.data;
  //         this.movieArray.push(array)
  //         console.log(this.movieArray);
  //     });
  //   },
  // },

  // created() {
  //   this.getApi();
  // }

}
</script>


<style scoped lang="scss">
img {
  width: 200px;
}
</style>
