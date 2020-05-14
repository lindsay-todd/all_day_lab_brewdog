<template lang="html">
<div>
  <li v-on:click="handleClick">{{beer.name}}</li>
  
</div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'list-item',
  props: ['beer', 'favouriteBeer'],
  methods: {
    handleClick(){
      eventBus.$emit('selected-beer', this.beer)
    }
    
  }
}
</script>

<style lang="css" scoped>
</style>