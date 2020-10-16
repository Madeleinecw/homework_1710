<template>
  <div id="app">
    <search-bar v-on:search-button-click='searchPokemon'>

    </search-bar>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue'
import { eventBus } from './main.js';

export default {
  name: 'App',
  components: {
    "search-bar": SearchBar
  },

  data() {
    return {
      pokemonList: [],
    }
  },

  created(){
    eventBus.$on('search-button-click', (value) => { //NEW
      this.searchPokemon(value);
    });
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

    searchPokemon(pokemon) {
      fetch(`https://pokeapi.co/api/v2/pokemon/${pokemon}`)
        .then(results => results.json())
        .then(data => console.log(data))
    }
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
