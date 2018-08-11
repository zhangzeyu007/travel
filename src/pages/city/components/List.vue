<template>

  <div class="List" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.currentCity}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper" v-for="item of hot" :key="item.id" v-on:click="handleCityClick(item.name)">
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item, key) of cities" :key="key" :ref="key">
        <div class="title border-topbottom">{{key}}</div>
        <div class="item-list" v-for="innerItem of item" >
          <div class="item border-bottom" :key="innerItem.id" v-on:click="handleCityClick(innerItem.name,innerItem.id)">
            {{innerItem.name}} {{innerItem.id}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'

export default {
  name: 'CityList',
  props: {
    cities: Object,
    hot: Array,
    letter: String
  },
  computed: {
    ...mapState({
      currentCity: 'city'})
  },
  watch: {
    letter () {
      console.log(this.letter)
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  },
  methods: {
    handleCityClick: function (city, id) {
      console.log('aaaaaa')
      //  this.$store.dispatch('changeCity', city)
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper,{click: true
    })
  }
}
</script>

<style lang="stylus" scoped>

  .border-topbottom
    &:before
      border-color: #ccc
    &:after
      border-color: #ccc

  .border-bottom
  &:before
    border-color: #ccc

  .List
    overflow: hidden
    position: absolute
    top: 1.68rem;
    left: 0
    right: 0;
    bottom: 0

  .title
    background: #eee
    line-height: .54rem;
    padding-left: .2rem;
    color: #666;
    font-size: .26rem;

  .button-list
    overflow: hidden;
    padding: .1rem .6rem .1rem .1rem;

  .button-wrapper
    width: 33.33%
    float: left

  .button
    margin: .1rem;
    text-align: center;
    border: .02rem solid #ccc;
    padding: .1rem 0;
    border-radius: .06rem;

  .item-list
    .item
      line-height: .76rem;
      padding-left: .2rem;

</style>
