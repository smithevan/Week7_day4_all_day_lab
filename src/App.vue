<template>
  <div>
    <beers-list :beers="beers"></beers-list> 
  </div>
</template>

<script>
import BeersList from './components/SelectedBeers.vue' //**imports the BeersList from SelectedBeers


export default {
  name: 'app',
  data() {
    return {
      beers: [{}], //beers array of objects
      selectedBeer: null, //object of the beer when it's selected
      favouriteBeer: null //object of the beer when it's been selected as favourite
    }
  },

  //Pulls in API data from API to the beers array of objects
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
      .then(res => res.json())
      .then(beers => this.beers = beers)
  },
  //not sure exactly
  components: {
    "beers-list": BeersList
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
