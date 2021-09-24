<template>
  <div>
    <Header @searchText="getInput"/>
    <Main :myQuery="inputText"/>
  </div>
</template>

<script>
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
      inputText:""
    }
  },
  methods: {
    getInput(text) {
      this.inputText = text;
      console.log(this.inputText)

    }
  }
}
</script>

<style lang="scss">
@import "./style/general.scss";
</style>
