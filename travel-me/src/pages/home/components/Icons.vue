<template>
  <div class="icons">
    <swiper class="icon-wrapper" :options="swiperOption">
      <swiper-slide v-for="(page, index) in pages" :key="index">
        <div class="item" v-for="(item,index) in page" :key="index">
          <img :src="item.imgUrl" class="icon-img">
          <p class="icon-title">{{item.title}}</p>
        </div>
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
    <div class="location-wrapper border-top">
      <div class="location border-right"><span class="iconfont icon-yanjizhushou-shangchuan_GPS"></span>定位失败</div>
      <div class="location"><span class="iconfont icon-world"></span>必游榜单</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  data () {
    return {
      swiperOption: {
        pagination: {
          el: '.swiper-pagination'
        }
      },
      iconList: [
        {
          title: '景点门票',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png'
        },
        {
          title: '文化古迹',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/20/831d62d2e1c7be02.png'
        },
        {
          title: '演出',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/e3/67df61427c8e1302.png'
        },
        {
          title: '一日游',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png'
        },
        {
          title: '西安必游',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png'
        },
        {
          title: '动植物园',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png'
        },
        {
          title: '打卡圣地',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/20/831d62d2e1c7be02.png'
        },
        {
          title: '兵马俑',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/fa/2548667cb6e902.png'
        },
        {
          title: '亲子游',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/50/26ffa31b56646402.png'
        },
        {
          title: '全部玩乐',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/80/416c6ab3368d1f02.png'
        }
      ]
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconList.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
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
