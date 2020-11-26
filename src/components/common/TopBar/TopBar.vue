<template>
  <div id="top-bar" :style="{background:bgColor}">
    <div class="top-bar-item left">
      <slot name="left"></slot>
    </div>
    <div class="top-bar-item center">
      <slot name="center"></slot>
    </div>
    <div class="top-bar-item right">
      <slot name="right"></slot>
    </div>
  </div>
</template>

<script>
  export default {
    name:"TopBar",
    props: {
      bgColor:{
        type:String,
        default:"#ff69b4"
      }
    }
  }
</script>

<style  scoped>
  #top-bar{
    width: 100%;
    height: 44px;
    display: flex;
  }
  .left , .right{
    width: 40px;
  }
  .center{
    flex: 1;
  }
</style>