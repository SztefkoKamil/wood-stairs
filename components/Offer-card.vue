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
  margin: 0 auto 50px;
  border-top-left-radius: 50px;
  border-top-right-radius: 50px;
  border-bottom-right-radius: 50px;
  max-width: 400px;

  &:last-child {
    margin-bottom: 0;
  }

  img {
    width: 100%;
    border-top-left-radius: 50px;
    border-bottom-right-radius: 50px;
    order: 2;
  }

  p {
    color: var(--font);
    padding: 20px 10px 30px;
  }

  &.reverse {
    border-bottom-right-radius: 0;
    border-top-right-radius: 50px;
    border-bottom-left-radius: 50px;

    img {
      border-bottom-right-radius: 0;
      border-bottom-left-radius: 50px;
      border-top-right-radius: 50px;
      order: 0;
    }
  }

  @media screen and (min-width: 768px) {
    & {
      display: flex;
      align-items: flex-end;
      max-width: 100%;
      height: 140px;
      margin-top: 145px;

      p {
        padding: 30px 20px 20px;
      }

      img {
        border-top-right-radius: 50px;
        width: 300px;
      }
    }

    &.reverse {
      margin-top: 120px;

      img {
        border-top-left-radius: 50px;
      }
    }
  }

  @media screen and (min-width: 910px) {
    & {
      p {
        font-size: 18px;
      }
    }
  }
}
</style>
