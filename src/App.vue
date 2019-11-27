<template lang="html">
<div>
<h1>Countries:</h1>
<div class="main-container">
<countries-list :countries='countries'></countries-list>
<country-info :country='selectedCountry'></country-info>
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
      this.selectedCountry = country;
    })
  },
  components:{
    "countries-list" : CountriesList,
    "country-info" : CountryInfo
  }
}
</script>

<style lang="css" scoped>
 .main-container{
   display: flex;
   justify-content: space-between;
 }

</style>
