<template lang="html">
  <div v-if="beers">
    <h3>{{beer.name}}</h3>
    <p>Description: {{beer.description}}</p>
    <p>ABV: {{beer.abv}}</p>
    <img :src="beer.image_url"/>
  </div>
</template>

<script>
export default {
  name: 'beer-detail',
  props:['beer']
}
</script>

<style lang="css" scoped>
</style>
