<template>
  <main class="w-75 my-5 mx-auto d-flex">
    <Card :movieList="movieList"/>
  </main>
</template>

<script>
import axios from 'axios'
import Card from './Card.vue'
export default {
  name: 'Main',
  components: {
    Card
  },
  props: {
    
  },
  data() {
    return {
      ApiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=cb82868cc612f450b5181bdf14387c5b&query=',
      myQuery: 'spider',
      movieList: []
    }
  },
  created() {
    this.getList()
  },
  methods: {
    getList() {
      axios
        // console.log((this.ApiUrl + this.myQuery))
        .get(this.ApiUrl + this.myQuery)
        .then(res => {
          console.log(res.data.results)
          this.movieList = res.data.results
        })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  main {
    background: blue;
  }
</style>
