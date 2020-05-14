<template>
  <div
    ref="preview"
    class="preview-container"
    tabindex="0"
    @keydown.esc="closePreview"
  >
    <button aria-label="close preview" @click="closePreview">
      <span></span>
      <span></span>
    </button>
    <img :src="src" alt="wooden stairs" />
  </div>
</template>

<script>
import eventBus from '../store/eventBus'

export default {
  props: ['name'],
  data() {
    return {
      src: '',
      images: [
        {
          name: 'about',
          src: require('../assets/images/about.webp')
        },
        {
          name: 'about-square',
          src: require('../assets/images/about-square.webp')
        },
        {
          name: 'offer-1',
          src: require('../assets/images/offer/offer-1.webp')
        },
        {
          name: 'offer-2',
          src: require('../assets/images/offer/offer-2.webp')
        },
        {
          name: 'offer-3',
          src: require('../assets/images/offer/offer-3.webp')
        },
        {
          name: 'g-1',
          src: require('../assets/images/gallery/g-1.webp')
        },
        {
          name: 'g-2',
          src: require('../assets/images/gallery/g-2.webp')
        },
        {
          name: 'g-3',
          src: require('../assets/images/gallery/g-3.webp')
        },
        {
          name: 'g-4',
          src: require('../assets/images/gallery/g-4.webp')
        },
        {
          name: 'g-5',
          src: require('../assets/images/gallery/g-5.webp')
        },
        {
          name: 'g-6',
          src: require('../assets/images/gallery/g-6.webp')
        },
        {
          name: 'g-7',
          src: require('../assets/images/gallery/g-7.webp')
        },
        {
          name: 'g-8',
          src: require('../assets/images/gallery/g-8.webp')
        },
        {
          name: 'g-9',
          src: require('../assets/images/gallery/g-9.webp')
        }
      ]
    }
  },
  beforeMount() {
    this.src = this.prepareSrc(this.name)
    this.$nextTick(() => this.$refs.preview.focus())
  },
  methods: {
    prepareSrc(name) {
      if (name === 'about-square' && window.innerWidth < 768) name = 'about'
      const img = this.images.find((img) => img.name === name)
      return img.src
    },
    closePreview() {
      eventBus.$emit('closePreview')
    }
  }
}
</script>

<style lang="scss">
.preview-container {
  height: 100vh;
  width: 100vw;
  position: fixed;
  top: 0;
  left: 0;
  background-color: var(--bg-primary);
  z-index: 100;
  overflow: scroll;

  &::-webkit-scrollbar {
    background-color: var(--bg-secondary);
  }
  &::-webkit-scrollbar-thumb {
    background-color: var(--bg-tertiary);
    border-radius: 15px;
  }

  button {
    position: fixed;
    top: 20px;
    right: 20px;
    width: 40px;
    height: 40px;
    border: none;
    background-color: var(--bg-secondary);
    border-radius: 50%;
    display: flex;
    flex-flow: column;
    justify-content: center;
    align-items: center;

    span {
      width: 30px;
      height: 4px;
      display: block;
      background-color: var(--color-primary);
      border-radius: 5px;

      &:first-child {
        transform: translateY(2px) rotate(45deg);
      }

      &:last-child {
        transform: translateY(-2px) rotate(-45deg);
      }
    }
  }
}
</style>
