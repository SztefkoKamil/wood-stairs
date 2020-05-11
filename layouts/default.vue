<template>
  <div>
    <Menu />
    <nuxt />
    <myFooter />
  </div>
</template>

<script>
import Menu from '../components/Menu'
import Footer from '../components/Footer'

export default {
  components: { Menu, myFooter: Footer }
}
</script>

<style>
html {
  font-family: 'Oswald', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
</style>
