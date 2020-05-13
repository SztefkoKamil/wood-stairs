<template>
  <header class="menu-container" :class="{ top }">
    <div class="wrapper">
      <a class="logo" href="#top">Wood-Stairs</a>
      <button @click="open = !open">
        <div class="toggle-menu-btn" :class="{ open }">
          <span></span>
          <span></span>
          <span></span>
        </div>
      </button>
      <nav :class="{ open }">
        <a class="section-anchor" href="#about" @click="active">ABOUT</a>
        <a class="section-anchor" href="#offer" @click="active">OFFER</a>
        <a class="section-anchor" href="#gallery" @click="active">GALLERY</a>
        <a class="section-anchor" href="#contact" @click="active">CONTACT</a>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      open: false,
      top: true
    }
  },
  beforeMount() {
    window.addEventListener('scroll', this.checkScrollY)
    this.checkScrollY()
  },
  methods: {
    checkScrollY() {
      const scrollY = window.scrollY
      if (scrollY > 200) this.top = false
      else this.top = true
    },
    active(e) {
      const anchors = [...document.querySelectorAll('.section-anchor')]
      this.open = false
      anchors.map((a) => {
        a.classList.remove('active')
      })
      e.target.classList.add('active')
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
  background-color: var(--menu-bg);
  z-index: 20;
  transition: background-color, 0.2s ease-in;

  .wrapper {
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 880px;
    height: 100%;
    margin: 0 auto;
    padding: 0 20px;
  }

  a {
    text-decoration: none;
    color: currentColor;
  }

  .logo {
    font-family: 'Permanent Marker';
    font-size: 26px;
  }

  nav {
    position: absolute;
    right: -210px;
    top: 49px;
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
      padding: 0 3px 2px;
      position: relative;

      &:first-child {
        margin-top: 40px;
      }

      &::after {
        content: '';
        position: absolute;
        bottom: 0;
        left: 0;
        border-bottom: 2px solid var(--green);
        width: 100%;
        transition: transform 0.2s ease-out;
        transform: scaleX(0);
      }

      &:hover::after {
        transform: scaleX(1);
      }

      &.active::after {
        transform: scaleX(1);
      }
    }

    &.open {
      transform: translateX(-210px);
    }
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

  @media screen and (min-width: 768px) {
    .wrapper {
      nav {
        position: static;
        flex-flow: row;
        height: auto;
        width: auto;

        a {
          margin: 0 0 0 24px;
        }
      }

      button {
        display: none;
      }
    }

    &.top {
      background-color: transparent;

      nav {
        background-color: transparent;
      }
    }
  }
}
</style>
