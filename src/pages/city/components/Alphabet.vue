<template>
  <ul class="list">
    <li class="item" v-for="item of letters" :key="item" :ref="item"
        @click="handlechange"
        @touchstart.prevent="handleTouchStart"
        @touchmove="handleTouchMove"
        @touchend="handleTouchEnd">
      {{item}}
    </li>
  </ul>
</template>

<script>
  export default {
    name: "CityALphabet",
    props: {
      cities: Object
    },
    data() {
      return {
        touchStatus: false,
        startY: 0,
        timer: null
      }
    },
    updated() {
      this.startY = this.$refs['A'][0].offsetTop;
    },
    computed: {
      letters() {
        const letters = []
        for (let i in this.cities) {
          letters.push(i)
        }
        return letters;
      }
    },
    methods: {
      handlechange: function (e) {
        this.$emit('change', e.target.innerText)
      },
      handleTouchStart: function () {
        this.touchStatus = true;
      },
      handleTouchMove: function (e) {

        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          if (this.touchStatus) {
            const touchY = e.touches[0].clientY - 79
            const index = Math.floor((touchY - this.startY) / 20)
            if (index >= 0 && index < this.letters.length) {
              console.log(this.letters[index])
              this.$emit('change', this.letters[index])
            }
          }
        })
      },
      handleTouchEnd: function () {
        this.touchStatus = false;
      }
    }
  }
</script>

<style lang="stylus" scoped>
  @import "~@/assets/styles/varibles.styl"
  .list
    z-index: 100
    display: flex;
    flex-direction: column
    justify-content: center;
    position: absolute
    top: 1.58rem
    right: 0
    bottom: 0;
    width: .4rem
    .item
      text-align: center;
      line-height: .4rem;
      color: $bgColor;


</style>
