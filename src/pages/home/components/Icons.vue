<template>
  <swiper :options="swiperOption">
    <swiper-slide v-for="(page,index) of pages" :key="index">
      <div class="Icons">
        <div class="Icon" v-for="item of page" :key="item.id">
          <div class="icon-img">
            <img class="icon-img-content" :src="item.imgUrl">
          </div>
          <p class="icon-desc">{{item.name}}</p>
        </div>
      </div>
    </swiper-slide>
  </swiper>
</template>

<script>

  export default {
    name: "HomeIcons",
    props: {
      iconList: Array
    },
    data() {
      return {
        swiperOption: {
          pagination: '.swiper-pagination',
          autoplay: false
        }
      }
    },
    computed: {
      pages() {
        const pages = [];
        this.iconList.forEach((item, index) => {
          const page = Math.floor(index / 8)
          if (!pages[page]) {
            pages[page] = [];
          }
          pages[page].push(item)
        })

        return pages
      }
    }
  }
</script>

<style lang="stylus" scoped>
  @import "~@/assets/styles/varibles.styl"
  @import "~@/assets/styles/mixins.styl"
  .Icons >>> .swiper-container
    height: 0;
    overflow: hidden;
    padding-bottom: 50%;

  .Icons
    overflow: hidden;
    height: 0;
    padding-bottom: 50%;
    margin-top: .1rem;
    .Icon
      position relative;
      overflow: hidden;
      width: 25%;
      padding-bottom: 25%;
      float: left;
      height: 0;
    .icon-img
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: .44rem;
      box-sizing: border-box;
      padding:, .1rem;
      .icon-img-content
        height: 100%;
        margin: 0 auto;
        display: block;

    .icon-desc
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      line-height: .44rem;
      height: .44rem;
      color: $daskTextColor;
      text-align: center;
      ellipsis()

</style>
