<template>
  <header class="menu-container" :class="{ top }">
    <div class="wrapper">
      <a class="logo" href="#top" aria-label="go to top">Wood-Stairs</a>
      <button aria-label="toggle mobile menu" @click="open = !open">
        <div class="toggle-menu-btn" :class="{ open }">
          <span></span>
          <span></span>
          <span></span>
        </div>
      </button>
      <nav role="menu" :class="{ open }">
        <a
          id="about-anchor"
          aria-label="about us section"
          role="menuitem"
          class="section-anchor"
          href="#about"
          @click="active"
          >ABOUT</a
        >
        <a
          id="offer-anchor"
          aria-label="offer section"
          role="menuitem"
          class="section-anchor"
          href="#offer"
          @click="active"
          >OFFER</a
        >
        <a
          id="gallery-anchor"
          aria-label="gallery section"
          role="menuitem"
          class="section-anchor"
          href="#gallery"
          @click="active"
          >GALLERY</a
        >
        <a
          id="contact-anchor"
          aria-label="contact section"
          role="menuitem"
          class="section-anchor"
          href="#contact"
          @click="active"
          >CONTACT</a
        >
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
    window.addEventListener('resize', this.checkScrollY)
    this.checkScrollY()
  },
  methods: {
    getAnchors() {
      const sections = {
        all: [...document.querySelectorAll('.section-anchor')],
        about: document.querySelector('#about-anchor'),
        offer: document.querySelector('#offer-anchor'),
        gallery: document.querySelector('#gallery-anchor'),
        contact: document.querySelector('#contact-anchor')
      }
      return sections
    },
    getSectionsPositions() {
      const about = document.querySelector('#about')
      const offer = document.querySelector('#offer')
      const gallery = document.querySelector('#gallery')
      const contact = document.querySelector('#contact')
      const sections = {
        about: about.offsetTop,
        offer: offer.offsetTop,
        gallery: gallery.offsetTop,
        contact: contact.offsetTop
      }
      return sections
    },
    checkScrollY() {
      const scrollY = window.scrollY
      if (scrollY > 200) this.top = false
      else this.top = true
      this.checkSection(scrollY)
    },
    active(e) {
      const anchors = this.getAnchors().all
      this.open = false
      anchors.map((a) => {
        a.classList.remove('active')
      })
      e.target.classList.add('active')
    },
    checkSection(scrollY) {
      const windowHeight = window.innerHeight
      const sections = this.getSectionsPositions()
      if (scrollY >= sections.contact - windowHeight * 0.5) {
        const anchors = this.getAnchors()
        anchors.all.map((a) => {
          a.classList.remove('active')
        })
        anchors.contact.classList.add('active')
      } else if (scrollY >= sections.gallery - windowHeight * 0.4) {
        const anchors = this.getAnchors()
        anchors.all.map((a) => {
          a.classList.remove('active')
        })
        anchors.gallery.classList.add('active')
      } else if (scrollY >= sections.offer - windowHeight * 0.4) {
        const anchors = this.getAnchors()
        anchors.all.map((a) => {
          a.classList.remove('active')
        })
        anchors.offer.classList.add('active')
      } else if (scrollY >= sections.about - windowHeight * 0.4) {
        const anchors = this.getAnchors()
        anchors.all.map((a) => {
          a.classList.remove('active')
        })
        anchors.about.classList.add('active')
      } else {
        const anchors = this.getAnchors()
        anchors.all.map((a) => {
          a.classList.remove('active')
        })
      }
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
  background-color: var(--bg-secondary);
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
    color: var(--color-primary);
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
    background: var(--bg-secondary);
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
        border-bottom: 2px solid var(--primary);
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
