<template>
  <div class="tabBar">
    <TabBarItem path="/home">
      <div slot="icon" class="fa fa-home item-icon"></div>
      <div slot="text">首页</div>
    </TabBarItem>
    <TabBarItem path="/category" col="#0ff">
      <div slot="icon" class="fa fa-th-large item-icon"></div>
      <div slot="text">分类</div>
    </TabBarItem>
    <TabBarItem path="cart" col="#f0f">
      <div slot="icon" class="fa fa-shopping-cart item-icon"></div>
      <div slot="text">购物车</div>
    </TabBarItem>
    <TabBarItem path="profile" col="#ff0">
      <div slot="icon" class="fa fa-user item-icon"></div>
      <div slot="text">我的</div>
    </TabBarItem>
  </div>
</template>

<script>
import TabBarItem from "./children/TabBarItem";

export default {
  name: "TabBar",
  components:{
    TabBarItem
  }
}
</script>

<style scoped>
  @import "../../../assets/css/font-awesome-4.7.0/css/font-awesome.min.css";
  .tabBar{
    position: fixed;
    bottom: 0px;
    left: 0px;
    right: 0px;
    height: 55px;
    display: flex;
    justify-content: space-around;
    text-align: center;
  }
  .tabBar .tab-bar-item{
    flex: 1;
    margin-top: 3px;
  }
  .tabBar .tab-bar-item .item-icon{
    font-size: 28px;
  }
</style>