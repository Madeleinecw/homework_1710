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
    data() {
        return {
            chartData: [],
            chartOptions: {}
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
            
            
    },
   
    // methods: {
    //     drawBasic(pokemon) {
    //         var data = google.visualization.arrayToDataTable([
    //             ['Stats', 'Stat Level',],
    //             ['HP', pokemon.stats[0].base_stat],
    //             ['Attack', pokemon.stats[1].base_stat],
    //             ['Defense', pokemon.stats[2].base_stat],
    //             ['Special Attack', pokemon.stats[3].base_stat],
    //             ['Special Defense', pokemon.stats[4].base_stat],
    //             ['Speed', pokemon.stats[5].base_stat]
    //         ]);

    //     var options = {
    //         title: 'Pokemon Strengths and Weaknesses',
    //         chartArea: {width: '50%'},
    //         hAxis: {
    //         title: 'Stat levels',
    //         minValue: 0
    //         },
    //         vAxis: {
    //         title: 'Stats'
    //         }
    //     };

    //     var chart = new google.visualization.BarChart(document.getElementById('chart_div'));
    //     chart.draw(data, options)
    // }
    // }
}
</script>

<style>

</style>