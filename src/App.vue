<template lang="html">
<div>
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
  },
  computed: {
  eventBus.$on('country-typed', (state) => {
    const result = this.countries.filter(nation => nation.name.includes(state))
    if (result.length === 1) {
     this.selectedCountry = result
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
}

 .main-container{
   display: flex;
   flex-direction: column;
   justify-content: space-between;
   align-items: center;
 }

</style>
