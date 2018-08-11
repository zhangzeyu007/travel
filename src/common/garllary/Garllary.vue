<template>
  <div  class="container" @click="handleClose">
    <div class="wrapper">
      <swiper :options="swiperOptions">
        <!-- slides -->
        <swiper-slide v-for="(item,index) of imgs" :key="index">
          <img class="garllar-img" :src="item">
        </swiper-slide>
        <!-- Optional controls -->
        <div class="swiper-pagination" slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'CommonGarllary',
    props: {
      imgs: {
        type: Array,
        default() {
          return []
        }
      }
    },
    data() {
      return {
        swiperOptions: {
          pagination: '.swiper-pagination',
          paginationType: 'fraction',
          observeParents: true,
          observer: true

        }
      }
    },
    methods: {
      handleClose () {
        this.$emit('close')
      }
    }
  }
</script>
<style lang="stylus" scoped>
  .container >>> .swiper-container {
    overflow: inherit;
  }

  .container {
    z-index 100
    display: flex;
    flex-direction: column;
    justify-content: center;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: #000;
  }

  .wrapper {
    background: #ffffff;
  }

  .garllar-img {
    width: 100%
  }

  .swiper-pagination {
    color: #ffffff;
    bottom: -1rem;
  }
</style>
