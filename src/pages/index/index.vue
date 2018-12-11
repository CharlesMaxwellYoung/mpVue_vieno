<template>
  <div class="home">
    <carousel :autoplay="autoplay" :interval="interval" :duration="duration" :circular="circular"
    :imgUrls="imgUrls" @swiper="showMore"></carousel>
    <slide :slide="slide"></slide>
    <bar pageId="home"></bar>
  </div>
</template>

<script>
  import bar from '@/components/bar'
  import carousel from '@/components/carousel'
  import slide from '@/components/slide'
  import poster from '@/components/poster'

  export default {
    data () {
      return {
        userInfo: {},
        autoplay: true,
        interval: 5000,
        duration: 900,
        circular: true,
        imgUrls: [
          'https://trailers.apple.com/trailers/home/promos/images/WebSpot1_1543975228.jpg',
          'https://trailers.apple.com/trailers/home/promos/images/WebSpot1_1537283191.jpg',
          'https://trailers.apple.com/trailers/home/promos/images/WebSpot1_1542929769.jpg'
        ],
        slide: {
          title: '新品推荐',
          more: '显示全部',
          posters: [
            {
              id: '1',
              url: 'https://trailers.apple.com/trailers/sony_pictures/spider-man-into-the-spider-verse/images/poster.jpg',
              width: 180,
              title: 'Spider-Man: Into The...',
              subtitle: ''
            },
            {
              id: '2',
              url: 'https://trailers.apple.com/trailers/wb/godzilla-king-of-the-monsters/images/poster.jpg',
              width: 180,
              title: 'Godzilla: King Of Th...',
              subtitle: ''
            }, {
              id: '3',
              url: 'https://trailers.apple.com/trailers/independent/swing-kids/images/poster.jpg',
              width: 180,
              title: 'Swing Kids',
              subtitle: ''
            }, {
              id: '4',
              url: 'https://trailers.apple.com/trailers/sony_pictures/the-intruder/images/poster.jpg',
              width: 180,
              title: 'The Intruder',
              subtitle: ''
            }, {
              id: '5',
              url: 'https://trailers.apple.com/trailers/sony_pictures/brightburn/images/poster.jpg',
              width: 180,
              title: 'Brightburn',
              subtitle: ''
            }, {
              id: '6',
              url: 'https://trailers.apple.com/trailers/magnolia/tyrel/images/poster.jpg',
              width: 180,
              title: 'Tyrel',
              subtitle: ''
            }]
        }
      }
    },

    components: {
      bar,
      carousel,
      slide,
      poster
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
  .home{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>
