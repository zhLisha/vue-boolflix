<template>
  <div class="container">
    <!-- Movie Section -->
    <div v-if="getArrayMovie.length" class="movie">
      <h2>Film</h2>
      <ul class="flex movie-section">
        <li class="card" v-for="item, index in getArrayMovie" :key="index">
          <!-- <img class="image-found" v-if="item.poster_path" :src="'https://image.tmdb.org/t/p/original/' + item.poster_path" :alt="item.title"> -->
          <img class="image-found" v-if="item.poster_path" :src="`https://image.tmdb.org/t/p/original${item.poster_path}`" :alt="item.title">
          <img class="not-found-image" v-else-if="item.poster_path == null" src="../assets/Image-Not-Available.png" alt="">
          <!-- Card Detailes activeted with hover -->
          <div class="hover-details">
            <div class="title">
              <span>Titolo: </span>
              {{item.title}}
            </div>
            <div class="original-title">
              <span>Titotlo Originale: </span>
              {{item.original_title}}
            </div>
            <div class="language flex">
              <span>Lingua: </span>
              <img class="flag" :src="getFlags(item.original_language)" :alt="item.original_laguage">
            </div>
            <div class="rated flex">
              <span>Voto: </span>
              
              <div class="stars">
                {{decimalNumber(item.vote_average)}}
                <i v-for="(star, index) in 5" :key="index" :class="{'yellow': star <= decimalNumber(item.vote_average)}" class="fa-solid fa-star"></i>
              </div>
            </div>
          </div>
        </li>
      </ul>
    </div>

    <!-- Tv Show Section -->
    <div v-if="getArrayTvShow.length" class="tv-show">
      <h2 class="tv-show-title">Serie</h2>
      <ul class="flex tv-show-section">
        <li class="card" v-for="item, index in getArrayTvShow" :key="index">
          <img class="image-found" v-if="item.poster_path" :src="`https://image.tmdb.org/t/p/original${item.poster_path}`" :alt="item.title">
          <img class="not-found-image" v-else-if="item.poster_path == null" src="../assets/Image-Not-Available.png" alt="">
          <!-- Card Detailes activeted with hover -->
          <div class="hover-details">
            <div class="title">
            <span>Titolo: </span>
            {{item.name}}
          </div>
          <div class="original-title">
            <span>Titotlo Originale: </span>
            {{item.original_name}}
          </div>
          <div class="language flex">
            <span>Lingua: </span>
            <img class="flag" :src="getFlags(item.original_language)" :alt="item.original_laguage">
          </div>
          <div class="rated flex">
            <span>Voto: </span>
            <div class="stars">
              <i v-for="(star, index) in 5" :key="index" :class="{'yellow': star <= decimalNumber(item.vote_average)}" class="fa-solid fa-star"></i>
            </div>
          </div>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>


export default {
  name: 'MainComp',
  props: {
    getArrayMovie: Array,
    getArrayTvShow: Array
  },
  data() {
    return {
      // getFlag: require('@/assets/Flags')
      ratingStar: [],
      ratingEmpty: []
    }
  },
  
  methods: {
    decimalNumber(number) {
      // Diviso il voto da 10 numeri a 5
       const removeDec = ( number / 2).toFixed();
      //  Ritrasformo da stringa a numero
       let numberVote = parseInt(removeDec)
       console.log('numeri prima', numberVote);

        return numberVote;
    },

    // Funzione per rendere uguali tutte le api language di TMDB e FLAGCND
    getFlags(flag) {
      if(flag == 'ja') {
        flag = 'jp';
      } else if( flag == 'en') {
        flag = 'gb';
      } else if (flag == 'hi' || flag == 'te') {
        flag = 'in';
      } else if (flag == 'zh') {
        flag = 'cn';
      } else if (flag == 'ko') {
        flag = 'kr';
      } else if( flag == 'da') {
        flag = 'dk';
      }

      return `https://flagcdn.com/w80/${flag}.png`
    }
  }
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
      margin: 20px 5px;
      width: calc((100% / 6) - 10px);
      position: relative;

      .hover-details{
        display: block;
        background-color: rgb(0, 0, 0);
        padding: 40px 20px;
        position: absolute;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
        transition: 0.5s;
        opacity: 0;
        overflow: auto;

        .title, .original-title, .language, .rated {
          padding: 8px;
        }

        .flag {
          width: 20px;
          padding-left: 10px;
        }
      }

      .not-found-image, .image-found{
        height: 100%;
      }

      // .image-found {
      //   height: 100%;
      // }

      span {
        font-size: 13px;
        font-weight: 500;
      
      }

      .rated {
        align-items: center;
        
        .stars {
          padding: 0 5px;
          .yellow {
          color: rgb(254, 225, 2);
        }

        .grey {
          color: rgb(173, 173, 173);
        }
        }
      }

      &:hover .hover-details{
        opacity: 1;
        background-color: rgba(0, 0, 0, 0.741)
      }
    }
  }
}
</style>
