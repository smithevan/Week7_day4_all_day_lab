<template>
  <div>
    <h1>Select A Beer</h1>
    <beers-list :beers="beers"></beers-list>  <!--uses the component beers-list to make html and binds beers to beers -->
    <beer-detail :selectedBeer="selectedBeer"></beer-detail>
  </div>
</template>

<script>
import BeersList from './components/SelectedBeers.vue' //**imports the BeersList from SelectedBeers
import BeerDetail from './components/SelectedBeerDetails.vue'
import { eventBus } from './main.js'

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
    //
    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
  })
},
  //takes BeersList from the import and assigns it to beers-list to be used as HTML tag above
  components: {
    "beers-list": BeersList,
    "beer-detail": BeerDetail
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
