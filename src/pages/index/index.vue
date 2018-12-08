<template>
  <div class="home">
    <carousel :autoplay="autoplay" :interval="interval" :duration="duration" :circular="circular"
              :imgUrls="imgUrls" @swiper="showMore"></carousel>
    <slide></slide>
    <bar pageId="home"></bar>
  </div>
</template>

<script>
  import bar from '@/components/bar'
  import carousel from '@/components/carousel'
  import slide from '@/components/slide'

  export default {
    data () {
      return {
        userInfo: {},
        autoplay: true,
        interval: 5000,
        duration: 900,
        circular: true,
        imgUrls: [
          'https://img1.doubanio.com/view/photo/l/public/p2199636259.webp',
          'https://img1.doubanio.com/view/photo/l/public/p2541926938.webp',
          'https://img1.doubanio.com/view/photo/l/public/p2522813488.webp'
        ]
      }
    },

    components: {
      bar,
      carousel,
      slide
    },

    methods: {
      showMore (e) {
        console.log(e)
      },
      bindViewTap () {
        const url = '../logs/main'
        wx.navigateTo({ url })
      },
      getUserInfo () {
        // 调用登录接口
        wx.login({
          success: () => {
            wx.getUserInfo({
              success: res => {
                this.userInfo = res.userInfo
              }
            })
          }
        })
      },
      clickHandle (msg, ev) {
        console.log('clickHandle:', msg, ev)
      }
    },

    created () {
      // 调用应用实例的方法获取全局数据
    }
  }
</script>

<style scoped>

</style>
