<template lang="html">
  <div>
    <h1>Beers</h1>
    <beers-list :beers='beers'></beers-list>
    <beer-detail :beer='selectedBeer'></beer-detail>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue'
import BeerDetail from './components/BeerDetail.vue'
import {eventBus} from './main.js'

export default {
  name: 'app',
  data(){
    return{
      beers: [],
      selectedBeer: null
    };
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer)=> {
      this.selectedBeer = beer;
    })
  },
  components: {
    "beers-list": BeersList,
    "beer-detail": BeerDetail
  }
}
</script>

<style lang="css" scoped>
</style>
