<template>
  <div>
    <home-header></home-header>
    <home-swiper></home-swiper>
    <home-icons></home-icons>
    <home-weekly-hot></home-weekly-hot>
    <home-you-like></home-you-like>
    <home-weekends></home-weekends>
    <home-footer></home-footer>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeWeeklyHot from './components/WeeklyHot'
import HomeYouLike from './components/YouLike'
import HomeWeekends from './components/Weekend'
import HomeFooter from './components/Footer'

export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeWeeklyHot,
    HomeYouLike,
    HomeWeekends,
    HomeFooter
  }
}
</script>

<style scoped>
</style>
