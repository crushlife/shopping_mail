<template>
  <div class="home-recommend">
    <div class="recommend-item" v-for="item in recommend" :key="item.sort">
      <a :href="item.link">
        <img :src="item.image" :alt="item.title">
        <p>{{item.title}}</p>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name:"HomeRecommend",
  props: {
    recommend:{
      type:Array
    }
  }

}
</script>

<style scoped>
  .home-recommend{
    display: flex;
    
  }
  .recommend-item{
    flex: 1;
    text-align: center;
    margin-top: 10px;
    padding-bottom: 10px;
    border-bottom: 5px solid #ccc;
  }
  .recommend-item img{
    width: 76px;
  }
  a{
    color: #333;
    font-size: 12px;
  }
</style>