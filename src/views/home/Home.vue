<template>
  <div id="home">
    <HomeTopBar></HomeTopBar>
    <div class="wrapper" ref="wrapper">
      <div class="content">
        <Swiper>
          <SwiperItem v-for="item in banner">
            <img :src="item.image" />
          </SwiperItem>
        </Swiper>
        <HomeRecommend :recommend="recommend"></HomeRecommend>
        <WeekPopular></WeekPopular>
        <TitleBar
          :titles="['流行', '新款', '精选']"
          @itemClick="itemClick">
        </TitleBar>
        <Goods :goods="goods[titles[currIndex]]"></Goods>
      </div>
    </div>
  </div>
</template>

<script>
// 导入公共组件
import { Swiper, SwiperItem } from "../../components/common/swiper";
import { request } from "../../network/axios";
import TitleBar from "../../components/content/TitleBar/TitleBar";
import Goods from "../../components/content/goods/Goods";
import BetterScroll from "better-scroll";

// 导入私有组件
import HomeTopBar from "./children/HomeTopBar";
import HomeRecommend from "./children/HomeRecommend";
import WeekPopular from "./children/WeekPopular";
import BScroll from "better-scroll";

export default {
  name: "Home",
  components: {
    HomeTopBar,
    Swiper,
    SwiperItem,
    HomeRecommend,
    WeekPopular,
    TitleBar,
    Goods,
  },
  data() {
    return {
      banner: [],
      recommend: [],
      goods: {
        pop: {
          title: "流行",
          id: 0,
          list: [],
        },
        news: {
          title: "新款",
          id: 0,
          list: [],
        },
        sell: {
          title: "精选",
          id: 0,
          list: [],
        },
      },
      titles: ["pop", "news", "sell"],
      currIndex: 0,
    };
  },
  methods: {
    getHomeMultidata() {
      request({
        url: "/home/multidata",
      }).then((res) => {
        this.banner = res.data.data.banner.list;
        this.recommend = res.data.data.recommend.list;
      });
    },
    getHomeGoodsInfo(title, id) {
      request({
        url: "/home/" + title,
        params: {
          id: id,
        },
      }).then((res) => {
        console.log(res);
        this.goods[title].list.push(...res.data.data.list);
        this.goods[title].id++;
        //console.log(this.goods[this.titles[this.currIndex]]);
        this.$nextTick( ()=> {
          const scroll = new BetterScroll(this.$refs.wrapper, {
            click:true,
            probeType:3,
            pullUpLoad:true
          })
          this.scroll = scroll
          this.scroll.on("pullingUp",(position) => {
            this.getHomeGoodsInfo(this.titles[this.currIndex], this.goods[this.titles[this.currIndex]].id + 1);
            
          })
       
        })
      });
    },
    itemClick(index) {
      this.currIndex = index;
      this.scroll.refresh()
    }
  },
  created() {
    this.getHomeMultidata();
    this.getHomeGoodsInfo("pop", this.goods.pop.id + 1);
    this.getHomeGoodsInfo("news", this.goods.news.id + 1);
    this.getHomeGoodsInfo("sell", this.goods.sell.id + 1);
  },
  mounted() {
  },
};
</script>

<style scoped>

.wrapper{
  height: calc(100vh - 50px - 44px);
  overflow: hidden;
}
</style>