<template lang="html">
  <div class="beer-detail" v-if="beer">
    <h3>{{beer.name}}</h3>
    <p>Description: {{beer.description}}</p>
    <p>ABV: {{beer.abv}}</p>
    <button @click="handleClick">Add To Favourites</button>
    <!-- <label for="favourite">Add to Favourites</label>
    <input @check="handleCheck" type="checkbox" id="favourite" value="Favourite"> -->
    <img :src="beer.image_url"/>
  </div>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name: 'beer-detail',
  props:['beer'],
  methods: {
    handleClick(){
      eventBus.$emit('add-to-favourites', this.beer)
    }
  }
}
</script>

<style lang="css" scoped>
img {
  height: 100px;
}
</style>
