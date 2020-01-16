<template lang="html">
  <div>
    <!-- <form v-on:submit.prevent> -->
      <select v-on:change="handleSelect" v-model="selectedBeer"> <!--v-model selectedBeer sends selected beer to event bus emitter-->
        <option v-for="(beer, index) in beers" :value="beer" key="index">{{beer.name}}</option>
        <!--looping over beer in beers with index, binding individual beer(banana/iterator) onto "beer",
        which gets used in the eventbus, and index is used as the hash key-->
      </select>
    <!-- </form> -->
  </div>

</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'beers-list',
  props: ['beers'],
  methods: {
    handleSelect(){
      eventBus.$emit('beer-selected', this.selectedBeer) //whatever is asked for in v-model is needed in event bus
    }
  }
}
</script>

<style lang="css" scoped>
</style>
