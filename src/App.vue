<template>
<div class="main-container">
  <h3>BEERS</h3>
  
  <div class="sub-container">
  <beer-list :beers="beers"></beer-list>
  <beer-detail :beer="selectedBeer"></beer-detail><button v-if="!favouriteBeer.includes(selectedBeer)" v-on:click="addToFavourites">Add Beer</button>
  
  
  </div>
</div>
</template>

<script>
import { eventBus } from './main.js'
import BeerList from './components/BeerList.vue'
import ListItem from './components/ListItem.vue'
import BeerDetail from './components/BeerDetail.vue'
import FavouritesList from './components/FavouritesList.vue'

export default {
  name: 'app',
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeer: []
    };
  },
  methods: {
    addToFavourites() {
      this.favouriteBeer.push(this.selectedBeer)
    }
  },
    components: {
    "beer-list": BeerList,
    "list-item": ListItem,
    "beer-detail": BeerDetail,
    "favourites-list": FavouritesList
  },

    mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('favourite-beer', (favouriteBeer) => {
      this.favouriteBeer = favouriteBeer
    })

    eventBus.$on('selected-beer', (beer) => {
      this.selectedBeer = beer
    })
  }

}
</script>
   
<style>
 .main-container {
    display: flex;
    justify-content: space-around;
    background-color: black;
    color: white;
  }
  .sub-container{
    background-color:red;
  }
</style>

