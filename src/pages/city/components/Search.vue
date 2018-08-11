<template>

  <div>
    <div class="search">
      <input type="text" v-model="keyWord" placeholder="输入城市名称或拼音" class="search-input"/>
    </div>
    <div class="search-content" ref="search" v-show="keyWord">
      <ul>
        <li class="search-item border-bottom" v-for="item of list" :key="item.id" @click="handleCityClick(item.name)">
          {{item.name}}
        </li>
        <li class="search-item border-bottom" v-show="hasNoData">没有匹配数据</li>
      </ul>
    </div>
  </div>
</template>

<script>
  import Bscroll from 'better-scroll'

  export default {
    name: "CitySearch",
    props: {
      cities: Object
    },
    data() {
      return {
        keyWord: '',
        timer: null,
        list: []
      }
    },
    methods: {
      handleCityClick(city) {
        this.$store.commit('changeCity', city)
        this.$router.push('/')

      }
    },
    computed: {
      hasNoData() {
        return !this.list.length
      }
    },
    watch: {
      keyWord() {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        if (!this.keyWord) {
          this.list = []
          return
        }
        this.timer = setTimeout(() => {
          const result = []
          for (let i in this.cities) {
            this.cities[i].forEach((value) => {
              if (value.spell.indexOf(this.keyWord) > -1 || value.name.indexOf(this.keyWord) > -1) {
                result.push(value)
              }

            })
          }
          this.list = result
        }, 100)
      }
    },
    mounted() {
      this.scroll = new Bscroll(this.$refs.search,{ click: true})

    }
  }
</script>

<style lang="stylus" scoped>
  @import '../../../assets/styles/varibles.styl';

  .search
    height: .72rem;
    background: $bgColor;
    padding: 0.1rem;
    .search-input
      height: .58rem;
      line-height: .62rem;
      text-align: center;
      width: 100%;
      border-radius: .06rem;
      color: #666;
      box-sizing: border-box
      padding: 0 .1rem

  .search-content
    z-index: 1
    overflow: hidden;
    position: absolute;
    top: 1.58rem;
    left: 0;
    bottom: 0;
    right: 0
    background: #eee;

  .search-item
    color: #666;
    line-height: .62rem
    padding-left: .2rem
    background: #ffffff;


</style>
