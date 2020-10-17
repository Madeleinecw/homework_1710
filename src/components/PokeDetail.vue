<template>
  <div>
      <h2>{{ pokemon.name }}</h2>
      <img :src="pokemon.sprites.front_default">
      <p v-for="(type, index) in pokemon.types" :key="index">Type: {{type.type.name}} </p>
      <p>Height: {{pokemon.height}}</p>
      <p>Weight: {{pokemon.weight}}</p>
      <poke-stats :pokemon='pokemon'></poke-stats>
  </div>
</template>

<script>
import { eventBus } from '../main.js'
import PokeStats from './PokeStats'

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

    methods: {
        searchPokemon(pokemon) {
        fetch(`https://pokeapi.co/api/v2/pokemon/${pokemon}`)
            .then(results => results.json())
            .then(data => this.pokemon = data)
        }
    }
}
</script>

<style>

</style>