<template>
  <div class="icons">
    <swiper class="icon-wrapper" :options="swiperOption">
      <swiper-slide v-for="(page, index) in pages" :key="index">
        <div class="item" v-for="(item, index) in page" :key="index">
          <img :src="item.imgUrl" class="icon-img" />
          <p class="icon-title">{{ item.title }}</p>
        </div>
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
    <div class="location-wrapper border-top">
      <div class="location border-right">
        <span class="iconfont icon-yanjizhushou-shangchuan_GPS"></span>定位失败
      </div>
      <div class="location">
        <span class="iconfont icon-world"></span>必游榜单
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeIcons",
  props: {
    iconList: Array
  },
  data() {
    return {
      swiperOption: {
        pagination: {
          el: ".swiper-pagination"
        }
      }
    };
  },
  computed: {
    pages() {
      const pages = [];
      this.iconList.forEach((item, index) => {
        const page = Math.floor(index / 8);
        if (!pages[page]) {
          pages[page] = [];
        }
        pages[page].push(item);
      });
      return pages;
    }
  }
};
</script>

<style scoped lang="stylus">
@import "~styles/variables.styl"
.icons >>> .swiper-pagination-bullet-active
  background-color $bgColor !important
.icons
  background-color #fff
.swiper-slide
  display flex
  flex-wrap wrap
  width 100%
  height 0
  padding-bottom calc(50%)
  overflow hidden
  .item
    overflow hidden
    padding-bottom calc(25% - .4rem)
    width 25%
    height 0
    .icon-img
      display block
      padding .1rem
      width calc(100% - 1.0rem)
      margin 0 auto
      margin-top .05rem
    .icon-title
      text-align center
      line-height .4rem
.location-wrapper
  display flex
  height 1rem
  line-height 1rem
  .location
    text-align center
    flex 1
</style>
