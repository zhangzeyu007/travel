<template>
  <div>
    <div class="recommend-title">
      <img class="mp-title-img" src="http://img1.qunarzz.com/piao/fusion/1711/89/ebc329f16c55bb02.png">
      <span class="mp-title">猜你喜欢</span>
    </div>
    <ul>
      <router-link tag="li" :to="'/detail/'+item.id" class="recommend-item border-bottom" v-for="item of  recommendList">
        <div class="recommend-imgcon">
          <img class="mp-like-img"
               :src="item.imgUrl">
        </div>
        <div class="recommend-info">
          <div class="mp-like-title">{{item.title}}</div>
          <!--评价-->
          <div class="mp-like-comment">
            <span class="mpf-starlevel">
              <strong :style="{width:item.star+'%'}"
                      class="iconfont  mpf-starlevel-gain">&#xe64b;&#xe64b;&#xe64b;&#xe64b;&#xe64b;</strong>
              <span class="iconfont  mpf-starlevel-total">&#xe64b;&#xe64b;&#xe64b;&#xe64b;&#xe64b;</span>
            </span>
            <span class="mp-comment-num">{{item.discuss}}</span>
          </div>
          <!--价格-->
          <div class="mp-like-price">
            <span class="mpg-price">
              ¥
              <em class="mpg-price-num">{{item.price}}</em>
            </span>
            起
            <span class="mp-like-address">{{item.address}}</span>
          </div>
          <!--提示-->
          <div class="mp-like-feature">
            <div class="mp-ellipsis2">{{item.feature}}</div>
          </div>
        </div>
      </router-link>
    </ul>
  </div>

</template>

<script>
  export default {
    name: "HomeRecommend",
    props: {
      recommendList: Array
    },
    data() {
      return {}
    }
  }
</script>

<style lang="stylus" scoped>
  @import "../../../assets/styles/mixins.styl"
  .recommend-title
    position: relative;
    padding: .24rem 0 .26rem;
    .mp-title-img
      display: inline-block;
      overflow: hidden;
      width: .3rem;
      height: .3rem;
      margin-left: .2rem;
      vertical-align: top;
    .mp-title
      display: inline-block;
      margin-left: .08rem;
      height: .44rem;
      color: #212121;
      font-size: .32rem;
      line-height: .44rem;

  .recommend-item
    overflow: hidden;
    display: flex
    position: relative;
    padding: .2rem 0;
    margin-left: .2rem;

    .recommend-imgcon
      float: left;
      overflow: hidden;
      width: 2rem;
      height: 2rem;
      background: #f0f5f8;

    .mp-like-img
      vertical-align: middle;
      width: 100%;

    .recommend-info
      overflow: hidden;
      padding-left: .22rem;
      flex: 1;
    .mp-like-title
      margin-top: .26rem;
      height: .44rem;
      color: #212121;
      font-size: .32rem;
      line-height: .44rem;
      ellipsis()
    .mpf-starlevel
      display: inline-block;
      position: relative;
      width: 1.5rem;
      height: .28rem;
      line-height: .28rem;
      font-size: .28rem;
      letter-spacing: .02rem;
    .mpf-starlevel-gain
      z-index: 2;
      color: #ffb436;
      overflow: hidden;
      position: absolute;
      top: .04rem;
      left: 0;
      height: .28rem;
      font-size: .28rem;
    .mpf-starlevel-total
      overflow: hidden;
      position: absolute;
      top: .04rem;
      left: 0;
      height: .28rem;
      z-index: 1;
      color: #e0e0e0;
      font-size: .28rem;
    .mp-comment-num
      color: #616161;
      font-size: .24rem;
      line-height: .34rem;
      vertical-align: text-bottom;
    .mp-like-price
      position: relative;
      margin-top: .22rem;
      color: #616161;
      font-size: .24rem;
      line-height: .4rem;
      .mpg-price
        color: #ff8300;
      .mpg-price-num
        font-size: .4rem;
      .mp-like-address
        position: absolute;
        right: .34rem;
        bottom: 0;

  .mp-like-feature
    display: inline-block;
    margin-top: .48rem;
    margin-right: .24rem;
    background: #fff9f9;
    padding: .04rem .1rem;
    color: #f55;
    font-size: .24rem;
    line-height: .34rem;

  .mp-ellipsis2
    display: -webkit-box;
    overflow: hidden;
    text-overflow: ellipsis;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;


</style>
