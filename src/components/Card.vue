<template>
  <div>
    <ul class="list-group">
      <li class="list-group-item">
        <div class="card-info">Titolo: {{ info.title }} </div>
        <div class="card-info">Titolo Originale: {{ info.original_title }}</div>
        <div class="card-info">Lingua: {{ info.original_language }}</div>
        <div class="card-info">Voto: {{ info.vote_average }}</div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: [
    'movieList',
    'info'
  ]
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  
</style>
