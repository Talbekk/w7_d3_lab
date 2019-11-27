<template lang="html">
  <div>
    <label for="country-select">Select a Country:</label>
    <select id="country-select" v-on:change="handleEvent" v-model="chosenCountry">
      <option disabled value="">Select Country</option>
      <option v-for="(country, index) in countries" :country='country' :key='index'>{{country.name}}</option>
    </select>
  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'countries-list',
  data(){
    return{
      chosenCountry: ""
    }
    },
  props: ['countries'],
  methods: {
    handleEvent(){
      eventBus.$emit('country-selected', this.chosenCountry)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
