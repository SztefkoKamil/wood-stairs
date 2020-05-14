<template>
  <article id="contact" class="contact-container section">
    <h2 class="section-header">Contact Us</h2>
    <div>
      <div class="address">
        <div>
          <svg
            aria-hidden="true"
            focusable="false"
            data-prefix="fas"
            data-icon="map-marked-alt"
            class="svg-inline--fa fa-map-marked-alt fa-w-18"
            role="img"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 576 512"
          >
            <path
              fill="#3EB115"
              d="M288 0c-69.59 0-126 56.41-126 126 0 56.26 82.35 158.8 113.9 196.02 6.39 7.54 17.82 7.54 24.2 0C331.65 284.8 414 182.26 414 126 414 56.41 357.59 0 288 0zm0 168c-23.2 0-42-18.8-42-42s18.8-42 42-42 42 18.8 42 42-18.8 42-42 42zM20.12 215.95A32.006 32.006 0 0 0 0 245.66v250.32c0 11.32 11.43 19.06 21.94 14.86L160 448V214.92c-8.84-15.98-16.07-31.54-21.25-46.42L20.12 215.95zM288 359.67c-14.07 0-27.38-6.18-36.51-16.96-19.66-23.2-40.57-49.62-59.49-76.72v182l192 64V266c-18.92 27.09-39.82 53.52-59.49 76.72-9.13 10.77-22.44 16.95-36.51 16.95zm266.06-198.51L416 224v288l139.88-55.95A31.996 31.996 0 0 0 576 426.34V176.02c0-11.32-11.43-19.06-21.94-14.86z"
            ></path>
          </svg>
          <h6>
            6405 Thornridge Cir undefined Jacksonville, Hawaii 80417 United
            States
          </h6>
        </div>
        <div>
          <svg
            aria-hidden="true"
            focusable="false"
            data-prefix="fas"
            data-icon="phone-alt"
            class="svg-inline--fa fa-phone-alt fa-w-16"
            role="img"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 512 512"
          >
            <path
              fill="#3EB115"
              d="M497.39 361.8l-112-48a24 24 0 0 0-28 6.9l-49.6 60.6A370.66 370.66 0 0 1 130.6 204.11l60.6-49.6a23.94 23.94 0 0 0 6.9-28l-48-112A24.16 24.16 0 0 0 122.6.61l-104 24A24 24 0 0 0 0 48c0 256.5 207.9 464 464 464a24 24 0 0 0 23.4-18.6l24-104a24.29 24.29 0 0 0-14.01-27.6z"
            ></path>
          </svg>
          <h6>(907) 555-0101</h6>
        </div>
        <div>
          <svg
            aria-hidden="true"
            focusable="false"
            data-prefix="fas"
            data-icon="envelope"
            class="svg-inline--fa fa-envelope fa-w-16"
            role="img"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 512 512"
          >
            <path
              fill="#3EB115"
              d="M502.3 190.8c3.9-3.1 9.7-.2 9.7 4.7V400c0 26.5-21.5 48-48 48H48c-26.5 0-48-21.5-48-48V195.6c0-5 5.7-7.8 9.7-4.7 22.4 17.4 52.1 39.5 154.1 113.6 21.1 15.4 56.7 47.8 92.2 47.6 35.7.3 72-32.8 92.3-47.6 102-74.1 131.6-96.3 154-113.7zM256 320c23.2.4 56.6-29.2 73.4-41.4 132.7-96.3 142.8-104.7 173.4-128.7 5.8-4.5 9.2-11.5 9.2-18.9v-19c0-26.5-21.5-48-48-48H48C21.5 64 0 85.5 0 112v19c0 7.4 3.4 14.3 9.2 18.9 30.6 23.9 40.7 32.4 173.4 128.7 16.8 12.2 50.2 41.8 73.4 41.4z"
            ></path>
          </svg>
          <h6>contact@wood-stairs.com</h6>
        </div>
      </div>
      <iframe
        id="iframeMap"
        title="map of our location"
        frameborder="0"
        scrolling="no"
        src=""
        data-src="https://www.openstreetmap.org/export/embed.html?bbox=-118.85614871978761%2C34.15663346692696%2C-118.82576465606691%2C34.187594858235826&amp;layer=mapnik&amp;marker=34.172115582379185%2C-118.84095668792725"
      ></iframe>
    </div>
  </article>
</template>

<script>
export default {
  mounted() {
    const iframe = document.querySelector('#iframeMap')
    const src = iframe.getAttribute('data-src')
    setTimeout(() => {
      iframe.setAttribute('src', src)
    }, 1000)
  }
}
</script>

<style lang="scss">
.contact-container {
  .address {
    & > div {
      display: flex;
      align-items: center;
      margin: 0 0 30px;

      &:last-child {
        margin: 0;
      }
    }

    svg {
      width: 50px;
    }

    h6 {
      font-weight: 400;
      font-size: 18px;
      margin: 0 0 0 20px;
    }
  }

  iframe {
    width: 100%;
    height: 60vw;
    margin: 50px 0 0;
  }

  @media screen and (min-width: 768px) {
    & > div {
      display: flex;
    }

    .address {
      width: 50%;
      padding: 0 20px 0 0;
    }

    iframe {
      width: 50%;
      height: 300px;
      margin: 0 0 0 20px;
    }
  }
}
</style>
