<template>
  <div class="tab-bar-item" @click="itemClick" :style="{color:changeColor}">
    <slot name="icon"></slot>
    <slot name="text"></slot>
  </div>
</template>

<script>
export default {
  name: "TabBarItem",
  props: {
    path:String,
    col:{
      type:String,
      default:"red"
    }
  },
  methods:{
    itemClick(){
      this.$router.push(this.path)
    }
  },
  computed: {
    isActive(){
      return this.$route.path.indexOf(this.path) !== -1 ? true : false
    },
    changeColor(){
      return this.isActive ? this.col : ""
    }
  }
}
</script>

<style scoped>
  .active{
    color: #f00;
  }
</style>