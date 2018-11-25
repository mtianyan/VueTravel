<template>
  <div>
    <city-header></city-header>
    <!--<city-header-options></city-header-options>-->
    <city-search :cities="cities"></city-search>
    <city-list :hotCities="hotCities" :cities="cities"></city-list>
  </div>
</template>

<script>
import CityHeader from './components/Header'
import CityHeaderOptions from './components/HeaderOptions'
import CityList from './components/List'
import CitySearch from './components/Search'

import axios from 'axios'
export default {
  name: 'City',
  data () {
    return {
      hotCities: [],
      cities: {}
    }
  },
  components: {
    CitySearch,
    CityHeader,
    CityHeaderOptions,
    CityList
  },
  methods: {
    getCityInfo () {
      axios.get('/api/city.json')
        .then(this.getCityInfoSucc)
    },
    getCityInfoSucc (res) {
      if (res.data.ret && res.data) {
        const data = res.data.data
        this.hotCities = data.hotCities
        this.cities = data.cities
      }
    }
  },
  mounted () {
    this.getCityInfo()
  }
}
</script>

<style scoped>
</style>
