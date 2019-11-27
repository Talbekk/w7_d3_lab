<template lang="html">
  <div v-if='country'>
    <div id="country-block">
    <h2>{{country.name}}</h2>
    <p><b>Capital:</b> {{country.capital}}</p>
    <p><b>Population:</b> {{country.population}}</p>
    <ul>
      <h3><b>Languages:</b></h3>
      <li v-for="language in country.languages">{{language.name}}</li>
    </ul>
    <img class="lrg-flag" :src="country.flag" />
    </div>
  </div>
</template>

<script>

import {eventBus} from '../main.js'

export default {
  name: 'country-info',
  props: ['country']
}

</script>

<style lang="css" scoped>
.lrg-flag {
  height: 100px;
}

#country-block {
  margin: 1rem 1rem;
  padding: 1rem 1rem;
  border: 1px solid #20437c;
  border-radius: 5%;
  display: inline-block;
  background-color: #21A1D3
}
</style>
