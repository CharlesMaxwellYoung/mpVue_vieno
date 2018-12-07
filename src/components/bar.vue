<template>
  <div class="bar">
    <ul class="bar__list">
      <li class="bar__item" v-for="item in bars" :key="item">
        <span class="item-text">{{item.name}}</span>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      bars: [
        { name: "首页", id: "home", icon: "" },
        { name: "直播", id: "live", icon: "" },
        { name: "点播", id: "vod", icon: "" },
        { name: "ME", id: "me", icon: "" }
      ]
    };
  }
};
</script>
<style lang="scss" scoped>
.bar {
  width: 100%;
  height: 100rpx;
  background: rgba(0, 0, 0, 0.7);
  position: fixed;
  bottom: 0;
  .bar__list {
    display: flex;
    justify-content: space-between;
    .bar__item {
      font-size: 20rpx;
      width: 100%;
      height: 100%;
      line-height: 100rpx;
      color: white;
      text-align: center;
      .item-text {
      }
    }
  }
}
</style>
