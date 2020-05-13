<template>
  <article id="offer" class="offer-container section">
    <div>
      <h2 class="section-header">What we offer</h2>
      <ul>
        <Card
          v-for="(card, i) in cards"
          :key="card.img"
          :card="card"
          :class="{ reverse: i % 2 ? true : false }"
        />
      </ul>
    </div>
  </article>
</template>

<script>
import Card from './Offer-card'

export default {
  components: { Card },
  data() {
    return {
      cards: [
        {
          name: 'offer-1',
          src: require('../assets/images/offer/thumbnail-offer-1.webp'),
          text:
            'Cupidatat dolore pariatur culpa quis minim dolore. Labore id enim ad proident esse consectetur Lorem mollit ut fugiat. Id eiusmod voluptate irure exercitation ex incididunt quis elit consequat.'
        },
        {
          name: 'offer-2',
          src: require('../assets/images/offer/thumbnail-offer-2.webp'),
          text:
            'Mollit qui duis ut sit non amet enim dolore adipisicing. Ea sit id proident eiusmod consectetur amet ea laborum id quis eu mollit dolore. Consequat enim nisi aliquip tempor veniam pariatur fugiat culpa officia esse.'
        },
        {
          name: 'offer-3',
          src: require('../assets/images/offer/thumbnail-offer-3.webp'),
          text:
            'Id aliqua minim ad eiusmod eu cupidatat qui nisi. Laboris ad nulla amet nostrud veniam id. Irure aliquip aute labore quis.  Lorem mollit ut fugiat.'
        }
      ]
    }
  }
}
</script>

<style lang="scss">
.offer-container {
  ul {
    list-style: none;
  }
}
</style>
