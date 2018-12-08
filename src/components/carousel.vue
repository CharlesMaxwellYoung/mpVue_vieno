<template>
  <div class="carousel" v-if="imgUrls.length>0">
    <swiper :autoplay="autoplay" :interval="interval" :duration="duration"
            :circular="circular">
      <div v-for="(item, index) in imgUrls" :key="index">
        <swiper-item>
          <img :src="item" class="slide-image" @click="targetPage"/>
        </swiper-item>
      </div>
    </swiper>
  </div>
</template>

<script>
  export default {
    name: 'carousel',
    props: ['autoplay', 'interval', 'duration', 'circular', 'imgUrls'],
    data () {
      return {}
    },
    methods: {
      targetPage (e) {
        this.$emit('swiper', e)
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import "../../static/style/_valid.scss";

  .carousel {
    width: 100%;
    height: unit(142);
    .slide-image {
      width: 100%;
    }
  }
</style>
