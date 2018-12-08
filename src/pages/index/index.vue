<template>
  <div class="index">
    <bar pageId="home"></bar>
  </div>
</template>

<script>
import card from "@/components/card";
import bar from "@/components/bar";

export default {
  data() {
    return {
      userInfo: {}
    };
  },

  components: {
    card,
    bar
  },

  methods: {
    bindViewTap() {
      const url = "../logs/main";
      wx.navigateTo({ url });
    },
    getUserInfo() {
      // 调用登录接口
      wx.login({
        success: () => {
          wx.getUserInfo({
            success: res => {
              this.userInfo = res.userInfo;
            }
          });
        }
      });
    },
    clickHandle(msg, ev) {
      console.log("clickHandle:", msg, ev);
    }
  },

  created() {
    // 调用应用实例的方法获取全局数据
  }
};
</script>

<style scoped>

</style>
