<template>
<div>
    <GChart
        type="BarChart"
        :data="this.chartData"
        :options="this.chartOptions"
    />
    <p></p>
  </div>
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
    name: 'poke-stats',
    props: ['pokemon'],
    components: {
    GChart
  },

  computed: {
    chartData: function(){        
        return [
            ['Stats', 'Stat Level',],
            ['HP', this.pokemon.stats[0].base_stat],
            ['Attack', this.pokemon.stats[1].base_stat],
            ['Defense', this.pokemon.stats[2].base_stat],
            ['Special Attack', this.pokemon.stats[3].base_stat],
            ['Special Defense', this.pokemon.stats[4].base_stat],
            ['Speed', this.pokemon.stats[5].base_stat]
        ]        
    },
    chartOptions: function(){
        return {
            chart: {
            title: 'Pokemon Stats',
            subtitle: 'How good is this Pokemon?',
            }
        }
    }
  },

    mounted(){
        
        this.chartData = [
            ['Stats', 'Stat Level',],
            ['HP', this.pokemon.stats[0].base_stat],
            ['Attack', this.pokemon.stats[1].base_stat],
            ['Defense', this.pokemon.stats[2].base_stat],
            ['Special Attack', this.pokemon.stats[3].base_stat],
            ['Special Defense', this.pokemon.stats[4].base_stat],
            ['Speed', this.pokemon.stats[5].base_stat]
        ]
        this.chartOptions = {
            chart: {
            title: 'Pokemon Stats',
            subtitle: 'How good is this Pokemon?',
            }
        }
            
            
    }
}
</script>

<style>

</style>