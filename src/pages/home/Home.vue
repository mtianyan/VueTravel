<template>
  <div>
    <home-header></home-header>
    <home-swiper :swiperList="swiperList"></home-swiper>
    <home-icons :iconList="iconList"></home-icons>
    <home-weekly-hot :hotList="hotList" :topIcon="topIcon"></home-weekly-hot>
    <home-you-like :itemList="itemList"></home-you-like>
    <home-weekends :weekendList="weekendList"></home-weekends>
    <home-footer></home-footer>
  </div>
</template>

<script>
import HomeHeader from "./components/Header";
import HomeSwiper from "./components/Swiper";
import HomeIcons from "./components/Icons";
import HomeWeeklyHot from "./components/WeeklyHot";
import HomeYouLike from "./components/YouLike";
import HomeWeekends from "./components/Weekend";
import HomeFooter from "./components/Footer";
import axios from "axios";
import { mapState } from "vuex";

export default {
  name: "Home",
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeWeeklyHot,
    HomeYouLike,
    HomeWeekends,
    HomeFooter
  },
  data() {
    return {
      swiperList: [],
      iconList: [],
      hotList: [],
      topIcon: [],
      itemList: [],
      weekendList: []
    };
  },
  computed: {
    ...mapState(["city"])
  },
  methods: {
    getHomeInfo() {
      axios.get("/api/index.json?city=" + this.city).then(this.getHomeInfoSucc);
    },
    getHomeInfoSucc(res) {
      if (res.data.ret && res.data.data) {
        const data = res.data.data;
        this.swiperList = data.swiperList;
        this.iconList = data.iconList;
        this.hotList = data.hotList;
        this.topIcon = data.topIcon;
        this.itemList = data.itemList;
        this.weekendList = data.weekendList;
      }
    }
  },
  mounted() {
    this.lastCity = this.city;
    this.getHomeInfo();
  },
  activated() {
    if (this.lastCity !== this.city) {
      this.lastCity = this.city;
      this.getHomeInfo();
    }
  }
};
</script>

<style scoped></style>
