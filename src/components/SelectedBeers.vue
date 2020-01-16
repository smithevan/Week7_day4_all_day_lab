<template lang="html">
  <div>
    <form v-on:submit.prevent>
      <select v-on: change="handleSelect" v-model="selectedBeer">
        <option v-for="(beer, index) in beers" :beer="beer" key="index">{{beer.name}}</option>
      </select>
    </form>
  </div>

</template>

<script>


export default {
  name: 'beers-list',
  props: ['beers']
}
</script>

<style lang="css" scoped>
</style>
