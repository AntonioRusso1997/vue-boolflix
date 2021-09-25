<template>
  <main class="container w-75 my-5 mx-auto d-flex flex-column">
    <h1 class="text-white">Film:</h1>
    <div class="row">
      <div class="col-2" v-for="(movie, index) in movieList" :key="index">
        <MovieCard  
        :infoMovie="movie" :movieList="movieList" :key="index"/>
      </div>
    </div>
    <h1 class="text-white">Serie TV:</h1>
    <div class="row">
      <div class="col-2" v-for="(tv, index) in tvList" :key="index">
        <TvSeriesCard  
        :infoTv="tv" :tvList="tvList" :key="index"/>
      </div>
    </div>
  </main>
</template>

<script>
import MovieCard from './MovieCard.vue'
import TvSeriesCard from './TvSeriesCard.vue'
export default {
  name: 'Main',
  components: {
    MovieCard,
    TvSeriesCard
  },
  props: [
    'movieList',
    'tvList',
  ]    
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../style/vars';
  
</style>
