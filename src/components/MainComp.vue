<template>
  <div class="container">
    <!-- Movie Section -->
    <h2>Film</h2>
    <ul class="flex movie-section">
      <li class="card" v-for="item, index in getArrayMovie" :key="index">
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
          {{item.original_language}}
        </div>
        <div class="rated">
          <span>Voto: </span>
          {{item.vote_average}}
        </div>
      </li>
    </ul>

    <!-- Tv Show Section -->
    <h2 class="tv-show-title">Serie</h2>
    <ul class="flex tv-show-section">
      <li class="card" v-for="item, index in getArrayTvShow" :key="index">
        <img :src="'https://image.tmdb.org/t/p/original/' + item.poster_path" :alt="item.title">
        <div class="title">
          <span>Titolo: </span>
          {{item.name}}
        </div>
        <div class="original-title">
          <span>Titotlo Originale: </span>
          {{item.original_name}}
        </div>
        <div class="language">
          <span>Lingua: </span>
          {{item.original_language}}
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
    getArrayMovie: Array,
    getArrayTvShow: Array
  },

}
</script>


<style scoped lang="scss">
@import '@/style/variables.scss';

.container {
  padding: 20px 0;
  h2 {
    color: white;
    border-bottom: 2px solid white;
  }

  .tv-show-title {
    padding-top: 30px;
  }
  .flex {
    flex-wrap: wrap;
    
    .card {
      font-size: 13px;
      font-weight: 100;
      color: white;
      padding: 20px 5px;
      width: calc((100% / 6) - 10px);

      span {
        font-size: 17px;
        font-weight: 500;
      }
      
    }
  }
}
</style>
