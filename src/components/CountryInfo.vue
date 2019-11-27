<template lang="html">
  <div v-if='country'>
    <h2>{{country.name}}</h2>
    <p><b>Capital:</b> {{country.capital}}</p>
    <p><b>Population:</b> {{country.population}}</p>
    <ul>
      <h3><b>Languages:</b></h3>
      <li v-for="language in country.languages">{{language.name}}</li>
    </ul>
    <img class="lrg-flag" :src="country.flag" />
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
</style>
