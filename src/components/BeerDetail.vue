<template lang='html'>
    <div v-if='beer'>
        <h3>{{beer.name}}</h3>
        <p>{{beer.tagline}}</p>
        <p><span>ABV: </span>{{beer.abv}}</p>
        <p><span>Description: </span>{{beer.description}}</p>
        <div v-if='favouriteBeer'></div>
        <h2> Favourite beer:{{favouriteBeer}}</h2>
    </div>
    
</template>

<script>
import { eventBus } from '../main.js';
export default {
    name: 'beer-detail',
    props: ['beer'],

}
</script>

<style>

</style>