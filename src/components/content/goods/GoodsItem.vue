<template>
  <div class="goodsItem">
    <img :src="item.show.img">
    <p class="title">{{item.title}}</p>
    <p>
      <span class="price">￥{{item.price}}</span>
      <img src="../../../assets/img/common/collect.svg">
      <span>{{item.cfav}}</span>
    </p>
  </div>
</template>

<script>
  export default {
    name:"GoodsItem",
    props: {
      item:Object
    }
  }
</script>

<style scoped>
  .goodsItem{
    width: 45%;
    margin-bottom: 20px;
  }
  .goodsItem>img{
    width: 100%;
  } 
  .goodsItem p{
    line-height: 26px;
  }
  .goodsItem p>img{
    width: 18px;
    margin-left: 45px;
  }
  .goodsItem .title{
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .goodsItem span{
    display: inline-block;
    vertical-align:middle;
  }
  .price{
    color: #f00;
    font-size: 12px;
  }
</style>