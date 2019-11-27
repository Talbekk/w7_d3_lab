<template lang="html">
  <div>
  <div id="menu">
    <label for="country-select">Select a Country: </label>
    <select id="country-select" v-on:change="handleEvent" v-model="chosenCountry">
      <option disabled value="">Select Country</option>
      <option v-for="(country, index) in countries" :country='country' :key='index'>{{country.name}}</option>
    </select>
  </div>
  <div id="search-bar">
    <form>
      <label for="search-bar">Type a country name</label>
    <input placeholder="Country Name" type="text" v-on:keyup="handleTyping" v-model="typedCountry"/>
    </form>
  </div>
  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'countries-list',
  data(){
    return{
      chosenCountry: "",
      typedCountry: ""
    }
    },
  props: ['countries'],
  methods: {
    handleEvent(){
      eventBus.$emit('country-selected', this.chosenCountry)
    },
    handleTyping(){
      eventBus.$emit('country-typed', this.typedCountry)
    }
  }
}
</script>

<style lang="css" scoped>

</style>
