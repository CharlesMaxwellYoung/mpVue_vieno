<template>
  <div class="bar">
    <ul class="bar__list">
      <li class="bar__item" v-for="(item,index) in bars" :key="index" @click="targetPage">
        <img class="bar__img" :src="item.icon" :alt="item.id">
        <span class="item-text" :class="{'active':pageId === item.id}">{{item.name}}</span>
      </li>
    </ul>
  </div>
</template>
<script>

  import utils from '@/utils'

  const iconsMap = {
    home: 'ios-star',
    live: 'ios-tv',
    vod: 'ios-film',
    me: 'ios-person'
  }
  export default {
    data () {
      return {
        bars: [
          { name: '首页', id: 'home', icon: utils.getIcon(iconsMap['home'] + '.svg') },
          { name: '直播', id: 'live', icon: utils.getIcon(iconsMap['live'] + '.svg') },
          { name: '点播', id: 'vod', icon: utils.getIcon(iconsMap['vod'] + '.svg') },
          { name: '我的', id: 'me', icon: utils.getIcon(iconsMap['me'] + '.svg') }
        ]
      }
    },
    props: ['pageId'],
    created () {
      if (this.pageId) {
        this.bars.forEach((item) => {
          if (item.id === this.pageId) {
            item.icon = utils.getIcon(iconsMap[item.id] + '-active.svg')
          }
        })
      }
    },
    methods: {
      targetPage (e) {
        console.log(e)
      }
    }
  }
</script>
<style lang="scss" scoped>
  @import "../../static/style/valid";

  .bar {
    width: 100%;
    height: unit(46);
    background-color: rgba(34,34,34,0.9);
    position: fixed;
    z-index: 6;
    bottom: 0;
    border-top: unit(1) solid #323232;
    .bar__list {
      display: flex;
      justify-content: space-between;
      margin-top: unit(5);
      .bar__item {
        width: 100%;
        color: #959595;
        text-align: center;
        display: flex;
        flex-direction: column;
        align-items: center;
        .item-text {
          font-size: unit(10);
        }
        .bar__img {
          width: unit(25);
          height: unit(25);
        }
      }
    }
  }

  .active {
    color: #00A0FC;
  }
</style>
