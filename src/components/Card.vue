<template>
  <div>
    <ul class="list-group">
      <li v-for="(movie, index) in movieList" :key="index" class="list-group-item">
        <div class="card-info">Titolo: {{ movie.title }} </div>
        <div class="card-info">Titolo Originale: {{ movie.original_title }}</div>
        <div class="card-info">Lingua: {{ movie.original_language }}</div>
        <div class="card-info">Voto: {{ movie.vote_average }}</div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: [
    'movieList'
  ]
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  
</style>
