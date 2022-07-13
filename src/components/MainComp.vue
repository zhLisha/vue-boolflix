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
          <!-- <img :src="`https://countryflagsapi.com/png/${item.original_laguage}`" :alt="item.original_laguage"> -->
        </div>
        <div class="rated flex">
          <span>Voto: </span>
          
          <div class="stars">
            {{decimalNumber(item.vote_average)}}
            <i v-for="(star, index) in ratingStar" :key="index" class="fa-solid fa-star yellow"></i>
            <i v-for="(star, index) in ratingEmpty" :key="index" class="fa-solid fa-star grey"></i>
          </div>
          <!-- {{item.vote_average}} -->
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
           <div class="stars">
            {{decimalNumber(item.vote_average)}}
            <i v-for="(star, index) in ratingStar" :key="index" class="fa-solid fa-star yellow"></i>
            <i v-for="(star, index) in ratingEmpty" :key="index" class="fa-solid fa-star grey"></i>
          </div>
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

      if(numberVote === 5) {
        this.ratingEmpty = [];
        this.ratingStar = [1, 1, 1, 1, 1];
        
      } else if(numberVote === 4) {
        this.ratingEmpty = [1];
        this.ratingStar = [1, 1, 1, 1];

      } else if(numberVote === 3) {
        this.ratingEmpty = [1, 1];
        this.ratingStar = [1, 1, 1];

      } else if(numberVote === 2) {
        this.ratingEmpty = [1, 1, 1];
        this.ratingStar = [1, 1]; 

      } else if( numberVote === 1) {
        this.ratingEmpty = [1, 1, 1, 1];
        this.ratingStar = [1];
      } else {
        this.ratingEmpty = [1, 1, 1, 1, 1];
        this.ratingStar = [];
      }
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
      padding: 20px 5px;
      width: calc((100% / 6) - 10px);

      span {
        font-size: 17px;
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
    }
  }
}
</style>
