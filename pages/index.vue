<template>
  <div class="container">
    <Hero />
    <main>
      <About />
      <Offer />
      <Gallery />
      <Contact />
    </main>
  </div>
</template>

<script>
import Hero from '../components/Hero'
import About from '../components/About'
import Offer from '../components/Offer'
import Gallery from '../components/Gallery'
import Contact from '../components/Contact'

export default {
  components: { Hero, About, Offer, Gallery, Contact }
}
</script>

<style lang="scss"></style>
