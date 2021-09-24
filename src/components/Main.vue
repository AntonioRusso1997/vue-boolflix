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
import axios from 'axios'
import Card from './Card.vue'
export default {
  name: 'Main',
  components: {
    Card
  },
  props: [
    'myQuery'
  ],
  data() {
    return {
      ApiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=cb82868cc612f450b5181bdf14387c5b',
      movieList: []
    }
  },
  created() {
    this.getList()
  },
  computed: {
    filteredMovieList() {
      if (this.myQuery === "") {
        return this.movieList
      }
      let filteredList = this.getList()
      return filteredList
    }
  },
  watch: { 
    myQuery: function() {
      this.getList();
      console.log("fdsgd")
    }
  },
  methods: {
    getList() {
      axios
        // console.log((this.ApiUrl + this.myQuery))
        .get(this.ApiUrl + (this.myQuery ? '&query=' + this.myQuery : ''))
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
  
</style>
