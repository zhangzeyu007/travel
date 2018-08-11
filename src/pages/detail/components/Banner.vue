<template>
 <div>
  <div class="banner" @click="handleGarllarClick">
   <img class="banner-img" :src="bannerImg">
   <div class="banner-info">
    <div class="banner-title">{{sightName}}</div>
    <div class="banner-number"><span class="iconfont banner-icon">&#xe600;</span>39</div>
   </div>
  </div>
  <common-fade>
   <common-garllary :imgs="gallaryImgs" v-show="GarllaryShow" @close="handleGarllarClose">
   </common-garllary>
  </common-fade>
 </div>
</template>

<script>
 import CommonGarllary from 'common/garllary/Garllary'
 import CommonFade from 'common/fade/Fade'

 export default {
  name: 'DetailBanner',
  props: {
   sightName: String,
   gallaryImgs: Array,
   bannerImg: String
  },
  data() {
   return {
    GarllaryShow: false
   }
  },
  components: {
   CommonGarllary,
   CommonFade
  },
  methods: {
   handleGarllarClick: function () {
    this.GarllaryShow = true
   },
   handleGarllarClose() {
    this.GarllaryShow = false
   }
  }
 }
</script>

<style scoped>
 .banner {
  overflow: hidden;
  height: 0;
  padding-bottom: 55%;
  position: relative;
 }

 .banner-img {
  width: 100%;
 }

 .banner-info {
  display: flex;
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  line-height: .6rem;
  color: #ffffff;
  background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, .8));
 }

 .banner-title {
  flex: 1;
  padding: 0 .2rem;
  font-size: .32rem;

 }

 .banner-number {
  margin-top: .14rem;
  padding: 0 .4rem;
  line-height: .32rem;
  height: .32rem;
  border-radius: .2rem;
  font-size: .24rem;
  background: rgba(0, 0, 0, .8);
 }

 .banner-icon {
  font-size: .20rem;
  margin-right: .1rem;
 }

</style>
