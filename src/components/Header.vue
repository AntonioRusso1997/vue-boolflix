<template>
  <header class="d-flex justify-content-between align-items-center px-5">
    <a href="/">
      <h2 class="fw-bold mt-2">BOOLFLIX</h2>
    </a>
    <div class="search-container d-flex">
      <input @keyup.enter="$emit('searchText', inputText)" v-model="inputText" class="form-control" type="search" placeholder="Cerca il tuo film preferito">
      <button @click.prevent="$emit('searchText', inputText)" type="submit" class="btn btn-danger">Cerca</button>
    </div>

  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
    
  },
  data() {
    return {
      inputText: "",
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../style/vars';

  header {
    height: 70px;
    background: black;

    a {
      color: $red;
      text-decoration: none;
    }
  }
</style>
