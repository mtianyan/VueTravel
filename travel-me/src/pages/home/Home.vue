<template>
  <div>
    <home-header></home-header>
    <home-swiper></home-swiper>
    <home-icons></home-icons>
    <home-weekly-hot></home-weekly-hot>
    <home-you-like></home-you-like>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeWeeklyHot from './components/WeeklyHot'
import HomeYouLike from './components/YouLike'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeWeeklyHot,
    HomeYouLike
  }
}
</script>

<style scoped>
</style>
