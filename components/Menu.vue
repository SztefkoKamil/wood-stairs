<template>
  <header class="menu-container">
    <a class="logo" href="#top">Wood-Stairs</a>
    <button v-if="!desktop" @click="open = !open">
      <div class="toggle-menu-btn" :class="{ open }">
        <span></span>
        <span></span>
        <span></span>
      </div>
    </button>
    <nav :class="{ open }">
      <a href="#about" @click="open = false">ABOUT</a>
      <a href="#offer" @click="open = false">OFFER</a>
      <a href="#gallery" @click="open = false">GALLERY</a>
      <a href="#contact" @click="open = false">CONTACT</a>
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      open: false,
      desktop: false
    }
  }
}
</script>

<style lang="scss">
.menu-container {
  position: fixed;
  top: 0;
  left: 0;
  height: 50px;
  width: 100%;
  background: var(--menu-bg);
  display: flex;
  justify-content: space-between;
  align-items: center;
  z-index: 20;
  padding: 0 20px;

  a {
    text-decoration: none;
    color: currentColor;
  }

  .logo {
    font-family: 'Permanent Marker';
    font-size: 26px;
  }

  button {
    border: none;
    background: none;
    height: 30px;
    width: 30px;

    .toggle-menu-btn {
      height: 100%;
      width: 100%;

      span {
        display: block;
        height: 3px;
        width: 30px;
        background: #fafafa;
        margin: 6px auto;
        transition: transform 0.2s ease-in, opacity 0.2s ease-in;
        transform-origin: center center;
      }

      &.open {
        span:first-child {
          transform: translateY(9px) rotate(45deg);
        }
        span:nth-child(2) {
          opacity: 0;
        }
        span:last-child {
          transform: translateY(-9px) rotate(-45deg);
        }
      }
    }
  }

  nav {
    position: absolute;
    right: -210px;
    top: 50px;
    display: flex;
    flex-flow: column;
    align-items: center;
    background: var(--menu-bg);
    width: 200px;
    height: 100vh;
    transition: transform 0.2s ease-in;

    a {
      font-size: 18px;
      margin-top: 30px;

      &:first-child {
        margin-top: 40px;
      }
    }

    &.open {
      transform: translateX(-210px);
    }
  }
}
</style>
