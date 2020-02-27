<template lang="html">
  <div class="flex-container">
      <div>
      <h1>Beers</h1>
      <beers-list :beers='beers'></beers-list>
      </div>

      <div class="beer-info">
      <beer-detail :beer='selectedBeer'></beer-detail>
      </div>

      <div>
      <h2>Favourite Beers</h2>
      <favourite-beers-list :beers='favourites'></favourite-beers-list>
      </div>
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
      selectedBeer: null,
      favourites: []

    };
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer)=> {
      this.selectedBeer = beer;
    })

    eventBus.$on('add-to-favourites',(beer) => {
      this.favourites.push(beer)
    })

  },
  components: {
    "beers-list": BeersList,
    "favourite-beers-list": BeersList,
    "beer-detail": BeerDetail
  }
}
</script>

<style lang="css" scoped>

.flex-container {
  display: flex;
  justify-content: space-between;
}

.beer-info {
  width: 300px;
}

</style>
