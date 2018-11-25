<template>
  <div class="list-item alphabet">
    <div class="title">字母排序</div>
    <div class="item-wrapper">
      <div class="item" v-for="item in alphabet" :key="item" @click="ChangeLetter(item)">{{item}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CityAlphabetLIst'
}
</script>

<style lang="stylus" scoped>
  &.alphabet
    .item-wrapper
    padding .3rem 0
    justify-content flex-start
    background-color #fff
    .item
      margin 0
      width calc(100% / 6)
</style>
