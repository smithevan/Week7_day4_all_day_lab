<template>
  <div>
    <h1>Test Text</h1>
  </div>
</template>

<script>
// import SelectedBeers from './components/SelectedBeers.vue'

export default {
  name: 'app',
  data() {
    return {
      beers: [{}],
      selectedBeer: null,
      favouriteBeer: null
    }
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
      .then(res => res.json())
      .then(beers => this.beers = beers)
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
