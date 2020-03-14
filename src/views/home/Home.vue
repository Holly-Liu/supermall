<template>
  <div>
    <nav-bar class="nav-bar">
      <span slot="center">购物街</span>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"></recommend-view>
  </div>
</template>

<script>
  import NavBar from 'common/navbar/NavBar'
  import HomeSwiper from "./childComps/HomeSwiper";
  import RecommendView from "./childComps/RecommendView";


  import {getHomeMultidata} from "../../network/home";

  export default {
    name: "Cart",
    data() {
      return {
        banners: [],
        recommends: []
      }
    },
    components: {
      NavBar,
      HomeSwiper,
      RecommendView
    },
    created() {
      getHomeMultidata().then(
          res => {
            this.banners = res.data.banner.list
            this.recommends = res.data.recommend.list
            console.log(res);
          }
      )
    }
  }
</script>

<style scoped>
  .nav-bar {
    background-color: var(--color-tint);
    color: #fff;
  }
</style>
