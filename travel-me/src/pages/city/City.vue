<template>
  <div>
    <city-header></city-header>
    <city-header-options></city-header-options>
    <city-search></city-search>
  </div>
</template>

<script>
import CityHeader from './components/Header'
import CityHeaderOptions from './components/HeaderOptions'
import CitySearch from './components/Search'
export default {
  name: 'City',
  components: {
    CityHeader,
    CitySearch,
    CityHeaderOptions
  }
}
</script>

<style scoped>

</style>
