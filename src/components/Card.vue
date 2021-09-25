<template>
  <div>
    <ul class="list-group">
      <li class="list-group-item">
        <div class="card-info">Titolo: {{ info.title }} </div>
        <div class="card-info">Titolo Originale: {{ info.original_title }}</div>
        <div class="card-info">Lingua: <CountryFlag :country='getFlag(info.original_language)' size='medium'/></div>
        <div class="card-info">Voto: {{ info.vote_average }}</div>
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
    'info'    
  ],
  methods: {
    getFlag (language) {
      return language
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  
</style>
