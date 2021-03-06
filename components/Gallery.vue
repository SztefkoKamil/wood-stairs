<template>
  <article id="gallery" class="gallery-container section">
    <h2 class="section-header">See our works</h2>
    <swiper
      ref="mySwiper"
      :options="swiperOptions"
      @resize="swiperSize(getWindowWidth())"
    >
      <swiper-slide v-for="(img, i) in images" :key="i">
        <img
          :src="img.src"
          :data-name="img.name"
          alt="wooden stairs"
          loading="lazy"
          @click="showPreview"
        />
      </swiper-slide>
      <div
        slot="button-prev"
        class="swiper-button-prev swiper-button"
        @keydown.space="showCurrentPreview"
      ></div>
      <div
        slot="button-next"
        ref="galleryNext"
        class="swiper-button-next swiper-button"
        @keydown.space="showCurrentPreview"
      ></div>
    </swiper>
  </article>
</template>

<script>
import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
import 'swiper/css/swiper.css'
import eventBus from '../store/eventBus'

export default {
  components: {
    Swiper,
    SwiperSlide
  },
  data() {
    return {
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
  created() {
    eventBus.$on('focusBack', (name) => {
      if (name.includes('g-'))
        this.$nextTick(() => this.$refs.galleryNext.focus())
    })
  },
  mounted() {
    this.swiperSize(this.getWindowWidth())
  },
  methods: {
    getWindowWidth: () => window.innerWidth,
    swiperSize(width) {
      const swiperOptions = this.$refs.mySwiper.swiperInstance.params
      if (width <= 560) swiperOptions.slidesPerView = 1
      else if (width <= 800) swiperOptions.slidesPerView = 2
      else swiperOptions.slidesPerView = 3
    },
    showPreview(e) {
      const name = e.target.getAttribute('data-name')
      eventBus.$emit('showPreview', name)
    },
    showCurrentPreview(e) {
      e.preventDefault()
      const current = document.querySelector('.swiper-slide-active img')
      current.click()
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
