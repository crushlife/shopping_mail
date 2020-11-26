<template>
  <div class="home">
    <HomeTopBar></HomeTopBar>
    <Swiper>
      <SwiperItem v-for="item in banner">
        <img :src="item.image">
      </SwiperItem>
    </Swiper>
    <HomeRecommend :recommend="recommend"></HomeRecommend>
  </div>
</template>

<script>
  // 导入公共组件
  import {Swiper,SwiperItem} from "../../components/common/swiper"
  import {request} from "../../network/axios";

  // 导入私有组件
  import HomeTopBar from "./children/HomeTopBar"
  import HomeRecommend from "./children/HomeRecommend"

  export default {
    name: "Home",
    components: {
      HomeTopBar,
      Swiper,
      SwiperItem,
      HomeRecommend
    },
    data(){
      return {
        banner:[],
        recommend:[]
      }
    },
    methods: {
      getHomeMultidata(){
        request({
          url:"/home/multidata"
        }).then(res => {
          this.banner = res.data.data.banner.list
          this.recommend = res.data.data.recommend.list
        })
      }
    },
    created () {
      this.getHomeMultidata()
    }
  }
</script>

<style scoped>
 
</style>