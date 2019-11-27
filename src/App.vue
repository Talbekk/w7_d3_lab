<template lang="html">
<div id="body">
<h1>Countries:</h1>
<div class="main-container">
<section id="chosen-country">
<country-info :country='selectedCountry'></country-info>
</section>
<section id="country-selector">
<countries-list :countries='countries'></countries-list>
</section>
</div>
</div>
</template>

<script>
import CountriesList from './components/CountriesList.vue';
import CountryInfo from './components/CountryInfo.vue';
import { eventBus } from './main.js';

export default {
  name: 'app',
  data(){
    return{
      countries: [],
      selectedCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)

    eventBus.$on('country-selected', (country) => {
      const result = this.countries.find(nation => nation.name === country)
      this.selectedCountry = result
    })
    eventBus.$on('country-typed', (country) => {
      const result = this.countries.filter(nation => nation.name.includes(country))
      if (result.length === 1) {
       this.selectedCountry = result[0]
      }
    })
  },
  components:{
    "countries-list" : CountriesList,
    "country-info" : CountryInfo
  }
}
</script>

<style lang="css" scoped>
h1 {
  display: flex;
  justify-content: center;
  background-color: #21A1D3
}

 .main-container{
   display: flex;
   flex-direction: row;
   justify-content: space-between;
   align-items: center;
 }
</style>
