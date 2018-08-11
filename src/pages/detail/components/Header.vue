<template>
  <div>
    <router-link tag="div" to="/" class="header-abs" v-show="showAbs">
      <div class="iconfont back-icon">&#xe624;</div>
    </router-link>
    <div class="header-fixed"
         v-show="!showAbs"
         :style="opacityStyle">
      <router-link to="/" tag="div" class="header-left">
        <div class="iconfont header-fiexed-back">&#xe624;</div>
      </router-link>
      景点详情
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 1
      }
    }
  },
  methods: {
    handleScroll () {
      let scrollTop = document.documentElement.scrollTop
      if (scrollTop > 60) {
        let opacity = scrollTop / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {opacity}
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeDestroy () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import "~@/assets/styles/varibles.styl"
  .header-abs {
    position: absolute;
    top: .2rem;
    left: .2rem;
    background: rgba(0, 0, 0, .8)
    height: .8rem;
    width: .8rem;
    border-radius: .8rem;
    line-height: .8rem;
    text-align: center;
  }

  .back-icon {
    color: #ffffff;
    font-size: .4rem;
  }
  .header-fixed
    position fixed;
    top: 0;
    left: 0;
    right: 0;
    overflow hidden;
    height: .86rem;
    line-height: .86rem;
    background-color: $bgColor;
    color: #ffffff;
    font-size: .32rem
    text-align: center;
    z-index: 10000

  .header-left
    position: absolute;
    top: 0;
    left: 0
    .header-fiexed-back
      color: #ffffff;
      width .64rem;
      text-align center;
      font-size: .4rem;

</style>
