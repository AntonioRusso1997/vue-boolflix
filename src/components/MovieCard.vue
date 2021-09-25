<template>
  <div>
    <ul class="list-group">
      <li class="list-group-item">
        <div class="card-info">Titolo: {{ infoMovie.title }} </div>
        <div class="card-info">Titolo Originale: {{ infoMovie.original_title }}</div>
        <div class="card-info">Lingua: <CountryFlag :country='getFlag(infoMovie.original_language)'/></div>
        <div class="card-info">Voto: {{ infoMovie.vote_average }}</div>
      </li>
    </ul>
  </div>
</template>

<script>
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
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  
</style>
