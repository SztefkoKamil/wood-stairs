<template>
  <article id="gallery" class="gallery-container">
    <h2 class="section-header">See our works</h2>
    <div>
      <swiper ref="mySwiper" :options="swiperOptions">
        <swiper-slide v-for="(img, i) in images" :key="i">
          <img :src="img" alt="wooden stairs" />
        </swiper-slide>
        <div slot="button-prev" class="swiper-button-prev swiper-button"></div>
        <div slot="button-next" class="swiper-button-next swiper-button"></div>
      </swiper>
    </div>
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
      swiperOptions: {
        loop: true,
        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev'
        }
      }
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
    }
  }
}
</style>
