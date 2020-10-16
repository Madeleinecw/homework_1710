<template>
    <div>
        <input id="search-bar" type="text" v-model="searchBar"/>
        <button id="choose-button" type="button" v-on:click="handleClick">I choose you!</button>
    </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name:'search-bar',
    props: [],
    data() {
        return {
            searchBar: ""
        }
    },
    mounted() {

    },
    methods: {
        handleClick() {
            eventBus.$emit('search-button-click', this.searchBar);                       
        }
       
    }
}
</script>

<style>

</style>