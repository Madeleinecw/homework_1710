<template>
  <div id="app">
    <search-bar></search-bar>
    <pokemon-detail></pokemon-detail>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue'
import PokemonDetail from './components/PokeDetail.vue'
import { eventBus } from './main.js';

export default {
  name: 'App',
  components: {
    "search-bar": SearchBar,
    "pokemon-detail": PokemonDetail,
  },

  data() {
    return {
      pokemonList: [],
      individualPokemon: []
    }
  },

  

  mounted() {
    this.GetAllPokemon();
  },

  methods: {
    GetAllPokemon() {
      fetch("https://pokeapi.co/api/v2/pokemon/")
        .then(results => results.json())
        .then(data => this.pokemonList = data.results)
    },

    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
