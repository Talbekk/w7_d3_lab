<template lang="html">
  <div id="main-block">
  <div id="menu-item">
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


#main-block {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin: 1rem 1rem;
  padding: 1rem 1rem;
  border: 1px solid #20437c;
  border-radius: 5%;
  display: inline-block;
  background-color: #21A1D3

}
#search-bar {
  margin: 0.5rem 0.5rem;
  padding: 0.5rem 0.5rem;
}

#menu-item {
  margin: 0.5rem 0.5rem;
  padding: 0.5rem 0.5rem;
}

</style>
