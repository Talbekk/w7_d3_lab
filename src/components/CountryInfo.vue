<template lang="html">
  <div v-if='country'>
    <h2>{{country.name}}</h2>
    <p>Capital: {{country.capital}}</p>
    <p>Population: {{country.population}}</p>
  </div>

</template>

<script>

import { eventBus } from '../main.js';

export default {
  name: 'country-info',
  props: ['country']
}

</script>

<style lang="css" scoped>
</style>
