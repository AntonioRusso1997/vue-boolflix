<template>
  <div>
    <ul class="list-group">
      <li class="list-group-item">
        <div class="card-image"> <img :src="getPoster(infoTv.poster_path)"> </div>
        <div class="card-info">Titolo: {{ infoTv.name }} </div>
        <div class="card-info">Titolo Originale: {{ infoTv.original_title }}</div>
        <div class="card-info">Lingua: <CountryFlag :country='getFlag(infoTv.original_language)'/></div>
        <div class="card-info"><span>Voto:</span> {{ getVote(infoTv.vote_average) }}</div>
      </li>
    </ul>
    
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
    'tvList',
    'infoTv'    
  ],
  data() {
    return {
      imageUrl: 'https://image.tmdb.org/t/p/original/',
      notFound: 'https://i.ibb.co/fGM9P8R/poster-not-avaiable.png'
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
      return vote
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

   .card-image {
    img {
      width: 100%;
    }
  }
</style>
