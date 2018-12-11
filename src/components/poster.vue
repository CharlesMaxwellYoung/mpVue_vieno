<template>
  <div class="poster" :style="{'width':width+'rpx'}" @click="showMore(id)">
    <div class="image">
      <div class="poster-default"></div>
      <img class="poster-cation" v-if="tvSrc!== ''" :src="tvSrc"/>
      <div class="poster-img" :style="{'width':width+'rpx','height':height+'rpx'}">
        <img class="img-main" :src="url" alt="">
      </div>
    </div>
    <div class="title">
      <div class="main-title" v-if="title!==''">{{title}}</div>
      <div class="subtitle" v-if="subtitle!== ''">{{subtitle}}</div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'poster',
    props: {
      width: {
        type: Number,
        default: 0
      },
      horizontal: {
        type: Boolean,
        default: false
      },

      url: {
        type: String,
        default: ''
      },
      id: {
        type: Number,
        default: 0
      },
      title: {
        type: String,
        default: ''
      },
      subtitle: {
        type: String,
        default: ''
      },
      tvSrc: {
        type: String,
        default: ''
      }
    },
    data () {
      return {
        height: 0
      }
    },
    created () {
      if (!this.horizontal) {
        this.height = this.width * 1.5;
      } else {
        this.height = this.width * 9 / 16;
      }
    },
    methods: {
      showMore (e) {
        this.$emit('onMore', e)
      }
    }
  }
</script>

<style scoped lang="scss">
  @import "../../static/style/valid";

  .poster {
    display: flex;
    flex-direction: column;
    margin-right: unit(15);
    .image {
      width: 100%;
      position: relative;
      .poster-default {
        position: absolute;
        top: 0;
        left: 0;
        height: 100%;
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        background: #323232 url("../../static/icons/ios-film.svg") no-repeat center;
        background-size: unit(40) unit(40);
        z-index: -1;
      }
      .poster-cation {
        position: absolute;
        z-index: 2;
        height: unit(20);
        width: unit(20);
        right: 0;
        bottom: 0;
      }
      .poster-img {
        .img-main {
          width: 100%;
          height: 100%;
        }
      }
    }
    .title {
      margin-top: unit(15);
      .main-title {

        font-size: unit(10);
        color: $white;
      }
      .subtitle {
        margin-top: unit(5);
        font-size: unit(10);
        color: $grey;
      }
    }
  }
</style>
