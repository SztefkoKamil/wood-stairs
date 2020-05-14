<template>
  <article id="gallery" class="gallery-container section">
    <h2 class="section-header">See our works</h2>
    <swiper v-if="show" ref="mySwiper" :options="swiperOptions">
      <swiper-slide v-for="(img, i) in images" :key="i">
        <img
          :src="img.src"
          :data-name="img.name"
          alt="wooden stairs"
          @click="showPreview"
        />
      </swiper-slide>
      <div slot="button-prev" class="swiper-button-prev swiper-button"></div>
      <div slot="button-next" class="swiper-button-next swiper-button"></div>
    </swiper>
  </article>
</template>

<script>
import { Swiper, SwiperSlide, directive } from 'vue-awesome-swiper'
import 'swiper/css/swiper.css'
import eventBus from '../store/eventBus'

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
        {
          name: 'g-1',
          src: require('../assets/images/gallery/thumbnail-g-1.webp')
        },
        {
          name: 'g-2',
          src: require('../assets/images/gallery/thumbnail-g-2.webp')
        },
        {
          name: 'g-3',
          src: require('../assets/images/gallery/thumbnail-g-3.webp')
        },
        {
          name: 'g-4',
          src: require('../assets/images/gallery/thumbnail-g-4.webp')
        },
        {
          name: 'g-5',
          src: require('../assets/images/gallery/thumbnail-g-5.webp')
        },
        {
          name: 'g-6',
          src: require('../assets/images/gallery/thumbnail-g-6.webp')
        },
        {
          name: 'g-7',
          src: require('../assets/images/gallery/thumbnail-g-7.webp')
        },
        {
          name: 'g-8',
          src: require('../assets/images/gallery/thumbnail-g-8.webp')
        },
        {
          name: 'g-9',
          src: require('../assets/images/gallery/thumbnail-g-9.webp')
        }
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
    showPreview(e) {
      const name = e.target.getAttribute('data-name')
      eventBus.$emit('showPreview', name)
    }
  }
}
</script>

<style lang="scss">
.gallery-container {
  .swiper-button {
    color: var(--primary);
  }

  .swiper-slide {
    img {
      width: 100%;
      cursor: pointer;
    }
  }
}
</style>
