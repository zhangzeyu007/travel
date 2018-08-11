<template>

 <div class="header">
  <div class="header-left">
   <router-link to="/">
    <div class="iconfont back-icon">&#xe624;</div>
   </router-link>
  </div>
  城市选择
 </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
 @import "~@/assets/styles/varibles.styl"
 .header
  position relative;
  overflow hidden;
  height: .86rem;
  line-height: .86rem;
  background-color: $bgColor;
  color: #ffffff;
  font-size: .32rem
  text-align: center;

 .header-left
  position: absolute;
  top: 0;
  left: 0
  .back-icon
   color: #ffffff;
   width .64rem;
   text-align center;
   font-size: .4rem;
</style>
