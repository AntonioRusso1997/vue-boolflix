<template>
  <main class="container w-75 my-5 mx-auto d-flex">
    <div class="row">
      <div class="col-2" v-for="(movie, index) in movieList" :key="index">
        <Card  
        :info="movie" :movieList="movieList" :key="index"/>
    </div>
    </div>
  </main>
</template>

<script>
import Card from './Card.vue'
export default {
  name: 'Main',
  components: {
    Card
  },
  props: [
    'movieList'
  ]    
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  
</style>
