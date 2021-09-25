<template>
  <div>
    <ul class="list-group">
      <li class="list-group-item">
        <div class="card-info">Titolo: {{ infoTv.name }} </div>
        <div class="card-info">Titolo Originale: {{ infoTv.original_title }}</div>
        <div class="card-info">Lingua: <CountryFlag :country='getFlag(infoTv.original_language)'/></div>
        <div class="card-info">Voto: {{ infoTv.vote_average }}</div>
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
    'tvList',
    'infoTv'    
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
