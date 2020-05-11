<template>
  <li class="card-container shadow-box">
    <img :src="card.img" alt="wooden-stairs" />
    <p>{{ card.text }}</p>
  </li>
</template>

<script>
export default {
  props: ['card']
}
</script>

<style lang="scss">
.card-container {
  background: var(--card-bg);
  margin: 0 0 50px;
  border-top-left-radius: 50px;
  border-bottom-right-radius: 50px;
  overflow: hidden;

  &:last-child {
    margin: 0;
  }

  img {
    width: 100%;
    border-bottom-right-radius: 50px;
  }

  p {
    color: var(--font);
    padding: 20px 10px 30px;
  }
}

.reverse {
  border-radius: 0;
  border-top-right-radius: 50px;
  border-bottom-left-radius: 50px;

  img {
    border-radius: 0;
    border-bottom-left-radius: 50px;
  }
}
</style>
