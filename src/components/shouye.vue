<template>
  <div class="wrapper">
    <div :class="matchContainerClass(i)" v-for="(item,i) in imgs" :key='item.id'>
      <div class="swiper-wrapper">
        <div class="swiper-slide" v-for="(itemImg,indexImg) in item.imgs" :key="indexImg">
          <img :src="itemImg"/>
        </div>
      </div>
      <div :class="matchPaginationClass(i)"></div>
    </div>
  </div>
</template>

<script>
  import Swiper from 'swiper'

  export default {
    name: 'shouye',
    data () {
      return {
        imgs: this.imgData
      }
    },
    props: {
      imgData: {
        type: Array,
        default: function () {
          return []
        }
      }
    },
    watch: {
      imgs () {
        this.initSwiper()
      }
    },
    created () {

    },
    methods: {
      matchContainerClass (i) {
        return `swiper-container swiper-container${i}`
      },
      matchPaginationClass (i) {
        return `swiper-pagination swiper-pagination${i}`
      },
      initSwiper () {
        this.$nextTick(() => {
          this.imgs.map((el, i) => {
            let swiper = `swiper${i}`
            let container = `.swiper-container${i}`
            let pagination = `.swiper-pagination${i}`
            this[swiper] = new Swiper(container, {
              loop: true,
              autoplay: {
                delay: 3000,
                disableOnInteraction: false
              },
              pagination: {
                el: pagination
              }
            })
          })
        })
      }
    },
    mounted () {
      this.initSwiper()
    }
  }
</script>

<style>
  .wrapper {
    width: 500px;
    margin: 20px auto;
  }

  .swiper-container {
    overflow: hidden;
  }

  img {
    width: 500px;
    height: 300px;
  }
</style>
