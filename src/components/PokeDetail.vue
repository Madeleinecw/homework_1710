<template>
<div>
    <h2>{{ pokemon.name }}</h2>
        <img :src="pokemon.sprites.front_default">
            <img :src="pokemon.sprites.back_default">
  <div id="flex-wrapper">
      
      <div id="item-1">
        <p v-for="(type, index) in pokemon.types" :key="index">Type: {{type.type.name}} </p>
        <p>Height: {{pokemon.height}}</p>
        <p>Weight: {{pokemon.weight}}g</p>
      </div>
        <div id="item-2">
        
        </div>
      <div id="item-3">
        <poke-stats :pokemon='pokemon'></poke-stats>
        
        </div>
    </div>
    </div>
</template>

<script>
import { eventBus } from '../main.js'
import PokeStats from './PokeStats'
import VueFlex from '../main.js'

export default {
    name: 'pokemon-detail',
    data() {
        return {
            pokemon: []
        }
    },
    components: {
        'poke-stats' : PokeStats
    },
    created(){
        eventBus.$on('search-button-click', (value) => { 
            this.searchPokemon(value);
        });
    },
    computed: { 
    },
    methods: {
        searchPokemon(pokemon) {
        fetch(`https://pokeapi.co/api/v2/pokemon/${pokemon}`)
            .then(results => results.json())
            .then(data => this.pokemon = data)
        },
    }
}
</script>

<style>
#flex-wrapper {
    display: flex;
    flex-direction: row nowrap;
    justify-content: center;
    margin-left: 60px;
    margin-right: 60px;
}
#item-1 {
    order: 1;
    padding: 20px
}
#item-2 {
    order: 2;
}
#item-3 {
    order: 3;
    padding: 20px;
}

</style>