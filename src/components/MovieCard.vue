<template>
  <div>
    <div class="flip-card">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <div class="card-image"> <img :src="getPoster(infoMovie.poster_path)"> </div>
        </div>
        <div class="flip-card-back">
          <div class="card-info"><b>Titolo:</b> {{ infoMovie.title }}</div>
          <div class="card-info"><b>Titolo Originale:</b> {{ infoMovie.original_title }}</div>
          <div class="card-info"><b>Lingua:</b> <CountryFlag :country='getFlag(infoMovie.original_language)'/></div>
          <div class="card-info"><b>Voto:</b> <span class="gold" v-html="getVote(infoMovie.vote_average)"></span> </div>
          <div class="card-info"><b>Overview:</b> {{ infoMovie.overview }} <div class="ellipsis">...</div></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import '@fortawesome/fontawesome-free/js/all.js';
import CountryFlag from 'vue-country-flag'
export default {
  name: 'Card',
  components: {
    CountryFlag
  },
  props: [
    'movieList',
    'infoMovie'    
  ],
  data() {
    return {
      imageUrl: 'https://image.tmdb.org/t/p/original/',
      notFound: 'https://i.ibb.co/fGM9P8R/poster-not-avaiable.png',
    }
  },
  methods: {
    getFlag (language) {
      if (language == "en") {
        return "gb"
      } else if (language == "ja") {
        return "jp"
      } else if (language == "zh") {
        return "ch"
      }
      return language
    },
    getPoster(path){
      if (path != null) {
        return this.imageUrl + path
      } else {
        return this.notFound
      }
    },
    getVote(vote){
      vote = vote / 2;
      vote = Math.floor(vote);
      let finalVote = '';
      for(let i = 0; i < vote; i++){
        finalVote += '<i class="fas fa-star"></i>';
      }
      return finalVote
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../style/vars';

  .flip-card {
  background-color: transparent;
  width: 100%;
  height: 290px;
  perspective: 1000px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  
  .card-image {
    width: 100%;
    height: 100%;
    overflow: hidden;
  }
  img {
    width: 100%;
  }
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(-180deg);
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
}

.flip-card-back {
  background-color: black;
  color: white;
  transform: rotateY(-180deg);
  padding: 20px;
  overflow: hidden;

    .card-info {
      font-size: 14px;
      margin: 5px 0;


      &:last-child {
        position: relative;
        height: 30px;
        text-overflow: ellipsis;
      }
      &:nth-child(3) {
        display: flex;
        align-items: center;
      }
    }
}   
  
</style>
