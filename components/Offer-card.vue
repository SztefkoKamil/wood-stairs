<template>
  <li class="card-container">
    <img
      :src="card.src"
      :data-name="card.name"
      alt="wooden-stairs"
      @click="showPreview"
    />
    <p>{{ card.text }}</p>
  </li>
</template>

<script>
import eventBus from '../store/eventBus'

export default {
  props: ['card'],
  methods: {
    showPreview(e) {
      const name = e.target.getAttribute('data-name')
      eventBus.$emit('showPreview', name)
    }
  }
}
</script>

<style lang="scss">
.card-container {
  background: var(--bg-tertiary);
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
    color: var(--color-secondary);
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
        cursor: pointer;
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
