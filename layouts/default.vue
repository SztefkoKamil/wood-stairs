<template>
  <div id="top">
    <Menu />
    <nuxt />
    <myFooter />
    <Preview v-if="preview" :name="name" />
  </div>
</template>

<script>
import eventBus from '../store/eventBus'
import Menu from '../components/Menu'
import Footer from '../components/Footer'
import Preview from '../components/Preview'

export default {
  components: { Menu, myFooter: Footer, Preview },
  data() {
    return {
      preview: false,
      name: ''
    }
  },
  beforeMount() {
    const html = document.querySelector('html')
    eventBus.$on('showPreview', (name) => {
      this.name = name
      html.classList.add('preview')
      this.preview = true
    })
    eventBus.$on('closePreview', () => {
      html.classList.remove('preview')
      this.preview = false
    })
  }
}
</script>

<style lang="scss">
html {
  font-family: 'Oswald', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  /* --- colors --- */
  background: #3d3d3d;
  color: #fafafa;
  --font: #363636;
  --menu-bg: #1c1c1c;
  --card-bg: #e9e9e9;
  --green: #3eb115;
  --shadow: hsla(0, 0%, 55%, 1);
  scroll-behavior: smooth;

  &.preview {
    overflow: hidden;
  }
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.section {
  padding: 70px 30px 0;
}

.section-header {
  font-size: 34px;
  font-family: 'Volkhov';
  font-weight: 400;
  text-align: center;
  width: max-content;
  margin: 0 auto 40px;
  padding: 0 0 3px 5px;
  position: relative;

  &:before {
    content: '';
    position: absolute;
    left: -5px;
    bottom: 0;
    height: 75%;
    width: 100%;
    border-left: 1px solid var(--green);
    border-bottom: 1px solid var(--green);
  }
}
</style>
