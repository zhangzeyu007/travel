<template>

  <div class="lazy-load">
    <h2 class="mp-modtitle">周末去哪儿</h2>
    <div>
      <div class="mp-product-item" v-for="item of weekendList">
        <div class="mp-product-img">
          <img :src="item.imgUrl">
        </div>
        <div class="mp-product-info">
          <p class="product-name">{{item.name}}</p>
          <p class="product-desc">{{item. desc}}</p>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
  export default {
    name: "HomeWeekend",
    props: {
      weekendList: Array
    },
    data() {
      return {}
    }
  }
</script>

<style lang="stylus" scoped>
  lazy-load {
    background #f5f5f5;
  }

  .mp-modtitle {
    height: .8rem;
    padding-left: .26rem;
    line-height: .8rem;
    color: #212121;
  }

  .mp-product-item {
    position: relative;
    margin-bottom: .1rem;
    background: #fff;
  }

  .mp-product-img {
    overflow: hidden;
    height: 0;
    padding-bottom: 37.4375%;
  }

  .mp-product-img img {
    width: 100%;
  }

  .mp-product-info {
    position: relative;
    padding: .14rem .2rem .2rem .2rem;

  }

  .product-name {
    overflow: hidden;
    padding-right: 1.4rem;
    color: #212121;
    font-size: .28rem;
    line-height: .48rem;
    white-space: nowrap;
    text-overflow: ellipsis;

  }

  .product-desc {
    overflow: hidden;
    padding-right: 1.4rem;
    color: #616161;
    font-size: .24rem;
    line-height: .42rem;
    white-space: nowrap;
    text-overflow: ellipsis;
  }

</style>
