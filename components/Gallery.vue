<template>
  <article id="gallery" class="gallery-container">
    <h2 class="section-header">See our works</h2>
    <swiper v-if="show" ref="mySwiper" :options="swiperOptions">
      <swiper-slide v-for="(img, i) in images" :key="i">
        <img :src="img" alt="wooden stairs" @click="showFullscreen" />
      </swiper-slide>
      <div slot="button-prev" class="swiper-button-prev swiper-button"></div>
      <div slot="button-next" class="swiper-button-next swiper-button"></div>
    </swiper>
  </article>
</template>

<script>
import { Swiper, SwiperSlide, directive } from 'vue-awesome-swiper'
import 'swiper/css/swiper.css'

export default {
  components: {
    Swiper,
    SwiperSlide
  },
  directives: {
    swiper: directive
  },
  data() {
    return {
      show: true,
      images: [
        require('../assets/images/gallery/thumbnail-g-1.webp'),
        require('../assets/images/gallery/thumbnail-g-2.webp'),
        require('../assets/images/gallery/thumbnail-g-3.webp'),
        require('../assets/images/gallery/thumbnail-g-4.webp'),
        require('../assets/images/gallery/thumbnail-g-5.webp'),
        require('../assets/images/gallery/thumbnail-g-6.webp'),
        require('../assets/images/gallery/thumbnail-g-7.webp'),
        require('../assets/images/gallery/thumbnail-g-8.webp'),
        require('../assets/images/gallery/thumbnail-g-9.webp')
      ],
      baseSwiper: null,
      swiperOptions: {
        loop: true,
        slidesPerView: 1,
        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev'
        }
      }
    }
  },
  beforeMount() {
    this.resizeListener()
    this.swiperSize(this.getWindowWidth())
  },
  methods: {
    getWindowWidth: () => window.innerWidth,
    resizeListener() {
      window.addEventListener('resize', () => {
        this.swiperSize(this.getWindowWidth())
      })
    },
    swiperSize(width) {
      if (width <= 560) {
        this.show = false
        this.swiperOptions.slidesPerView = 1
        this.$nextTick().then(() => {
          this.show = true
        })
      } else if (width <= 800) {
        this.show = false
        this.swiperOptions.slidesPerView = 2
        this.$nextTick().then(() => {
          this.show = true
        })
      } else {
        this.show = false
        this.swiperOptions.slidesPerView = 3
        this.$nextTick().then(() => {
          this.show = true
        })
      }
    },
    showFullscreen(e) {
      // console.log(e.target)
    }
  }
}
</script>

<style lang="scss">
.gallery-container {
  padding: 70px 30px 0;

  .swiper-button {
    color: var(--green);
  }

  .swiper-slide {
    img {
      width: 100%;
      cursor: pointer;
    }
  }
}
</style>
