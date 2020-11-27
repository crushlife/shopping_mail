<template>
  <div class="title-bar">
    <div class="title-item" 
         v-for="(item,index)  in titles" 
         :key="item" 
         @click="changeStyle(index)">
      <span :class="{active:currIndex == index ? true : false}">{{item}}</span>
      </div>
  </div>
</template>

<script>
  export default {
    name:"TitleBar",
    props: {
      titles:{
        type:Array
      }
    },
    data(){
      return {
        currIndex:0
      }
    },
    methods: {
      changeStyle(index){
        this.currIndex = index; 
        this.$emit("itemClick",index)
      }
    }
  }
</script>

<style scoped>
  .title-bar{
    display: flex;
    height: 48px;
    line-height: 48px;
  }
  .title-item{
    flex: 1;
    text-align: center;
    font-size: 18px;
  }
  .active{
    color: #ff69b4;
    border-bottom: 3px solid #ff69b4;
    padding-right: 5px;
    padding-left: 5px;
  }
</style>