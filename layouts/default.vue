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
      eventBus.$emit('focusBack', this.name)
    })
  }
}
</script>

<style lang="scss">
html {
  /* --- variables --- */
  --font-primary: 'Lato';
  --font-secondary: 'Volkhov';
  --color-primary: #fafafa;
  --color-secondary: #363636;
  --bg-primary: #3d3d3d;
  --bg-secondary: #1c1c1c;
  --bg-tertiary: #e9e9e9;
  --primary: #3eb115;
  /** --- global styles --- */
  font-family: var(--font-primary), Arial, sans-serif;
  font-size: 16px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  background: var(--bg-primary);
  background: linear-gradient(
    to right,
    #575757 0%,
    #3d3d3d 30%,
    #3d3d3d 70%,
    #575757 100%
  );
  color: var(--color-primary);
  scroll-behavior: smooth;

  &::-webkit-scrollbar {
    background-color: var(--bg-secondary);
  }
  &::-webkit-scrollbar-thumb {
    background-color: var(--bg-tertiary);
    border-radius: 15px;
  }

  &.preview {
    overflow: hidden;
  }

  p {
    line-height: 135%;
  }
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

*:focus {
  outline: 2px solid var(--primary);
}

.section {
  padding: 70px 30px 0;
}

.section-header {
  font-size: 34px;
  font-family: var(--font-secondary);
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
    border-left: 1px solid var(--primary);
    border-bottom: 1px solid var(--primary);
  }
}
</style>
