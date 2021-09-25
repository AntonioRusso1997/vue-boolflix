<template>
  <div>
    <Header @searchText="getInput"/>
    <Main :movieList="movieList"
          :tvList="tvList"
          />
  </div>
</template>

<script>
import axios from 'axios'
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
    return {
      inputText:"",
      // ApiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=cb82868cc612f450b5181bdf14387c5b',
      ApiUrl: 'https://api.themoviedb.org/3/search/',
      ApiMovie: "movie",
      ApiSeries: "tv",
      ApiKey: "?api_key=cb82868cc612f450b5181bdf14387c5b",
      movieList: [],
      tvList: []
    }
  },
  created() {
    this.getListMovie()
    this.getListTv()
  },
  computed: {
    filteredMovieList() {
      if (this.myQuery === "") {
        return this.movieList
      }
      let filteredList = this.getListMovie()
      return filteredList
    },
    filteredTvList() {
      if (this.myQuery === "") {
        return this.tvList
      }
      let filteredTvList = this.getListTv()
      return filteredTvList
    }
  },
  methods: {
    getInput(text) {
      this.inputText = text;
      console.log(this.inputText)
      this.getListMovie()
      this.getListTv()
    },
    getListMovie() {
      axios
        // console.log((this.ApiUrl + this.myQuery))
        .get(this.ApiUrl + this.ApiMovie + this.ApiKey + (this.inputText ? '&query=' + this.inputText : ''))
        .then(res => {
          // console.log(res.data.results)
          this.movieList = res.data.results
        })
    },
    getListTv() {
      axios
        .get(this.ApiUrl + this.ApiSeries + this.ApiKey + (this.inputText ? '&query=' + this.inputText : ''))
        .then(res => {
          // console.log(res.data.results)
          this.tvList = res.data.results
        })
    },
    
  }
}
</script>

<style lang="scss">
@import "./style/general.scss";
</style>
