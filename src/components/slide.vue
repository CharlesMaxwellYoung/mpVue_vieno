<template>
  <div class="slide">
    <div class="slide__header">
      <div class="header-title">{{slide.title}}</div>
      <div class="header-more">
        <div class="more-text">{{slide.more}}</div>
        <img class="more-icon" src="../../static/icons/ios-arrow-right.svg">
      </div>
    </div>
    <div class="slide-container">
      <scroll-view class="scroll-view_H" :scroll-x="true" style="width: 100%" v-if="slide.posters.length>0">
        <div class="poster">
          <poster v-for="(poster,index) in slide.posters" :key="index"
                  :url="poster.url"
                  :title="poster.title"
                  :width="poster.width"
                  :subtitle="poster.subtitle"
                  :tvSrc="poster.tvSrc"></poster>
        </div>
      </scroll-view>
    </div>
  </div>
</template>

<script>
  import poster from '@/components/poster'

  export default {
    name: 'slide',
    components: {
      poster
    },
    props: {
      slide: {
        type: Object,
        default: function () {
          return {
            title: '',
            more: '',
            posters: []
          }
        }
      }
    },
    data () {
      return {}
    }
  }
</script>

<style scoped lang="scss">
  @import "../../static/style/_valid.scss";

  .slide {
    color: $white;
    width: calc(100% - 60rpx);
    .slide__header {
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      .header-title {
        font-size: unit(15);
      }
      .header-more {
        font-size: unit(10);
        color: $grey;
        display: flex;
        height: unit(10);
        align-items: center;
        .more-icon{
          width: unit(10);
          height: unit(10);
        }
      }
    }

    .slide-container {
      margin-top: unit(20);
      .scroll-view_H {
        .poster {
          display: flex;
          flex-direction: row;
        }
      }
    }
  }
</style>
