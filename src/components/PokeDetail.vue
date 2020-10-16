<template>
  <div>
      <h2>{{ pokemon.name }}</h2>
  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'pokemon-detail',
    data() {
        return {
            pokemon: []
        }
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