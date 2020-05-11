<template>
  <article id="contact" class="contact-container">
    <h2 class="section-header">Contact Us</h2>
    <div>
      <div class="address">
        <div>
          <img src="../assets/images/icon-map.svg" alt="" />
          <h6>
            6405 Thornridge Cir undefined Jacksonville, Hawaii 80417 United
            States
          </h6>
        </div>
        <div>
          <img src="../assets/images/icon-phone.svg" alt="" />
          <h6>(907) 555-0101</h6>
        </div>
        <div>
          <img src="../assets/images/icon-mail.svg" alt="" />
          <h6>contact@wood-stairs.com</h6>
        </div>
      </div>
      <iframe
        frameborder="0"
        scrolling="no"
        src="https://www.openstreetmap.org/export/embed.html?bbox=-118.85614871978761%2C34.15663346692696%2C-118.82576465606691%2C34.187594858235826&amp;layer=mapnik&amp;marker=34.172115582379185%2C-118.84095668792725"
      ></iframe>
    </div>
  </article>
</template>

<style lang="scss">
.contact-container {
  padding: 70px 30px 0;

  .address {
    & > div {
      display: flex;
      align-items: center;
      margin: 0 0 30px;

      &:last-child {
        margin: 0;
      }
    }

    img {
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
