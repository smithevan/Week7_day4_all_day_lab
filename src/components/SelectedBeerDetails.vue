<template lang="html">
  <div v-if="selectedBeer" id="beerDetail">
    <h2>{{selectedBeer.name}}</h2>
    <p><span>Description</span>: {{selectedBeer.description}}</p>
    <p></p>
    <p></p>
  </div>
</template>

<script>



export default {
  name: 'beer-detail',
  props: ['selectedBeer']
  }

</script>

<style lang="css" scoped>
</style>
