<template>
  <article id="about" class="about-container section">
    <div>
      <h2 class="section-header">Who we are</h2>
      <div class="inner">
        <p>
          Culpa culpa duis in et deserunt proident exercitation velit do magna
          laborum. Veniam excepteur voluptate aliqua sunt aute eu cillum qui
          exercitation eiusmod mollit proident. Enim amet reprehenderit quis
          aliquip laborum esse deserunt. Commodo id labore est ad nisi occaecat
          sint incididunt pariatur eiusmod.
        </p>
        <picture>
          <source
            media="(max-width: 768px)"
            srcset="../assets/images/thumbnail-about.webp"
          />
          <img
            class="shadow-box"
            src="../assets/images/thumbnail-about-square.webp"
            alt="wooden stairs"
          />
        </picture>
      </div>
      <p>
        In Lorem ex est proident eiusmod id eu tempor. Minim officia sit
        incididunt enim ea labore aliqua enim amet velit nulla ex. Dolore ad
        laboris deserunt elit irure culpa tempor aliquip incididunt dolore
        proident laboris enim. Reprehenderit quis adipisicing aliquip cupidatat
        et sint laborum fugiat cupidatat excepteur occaecat in elit. Labore ad
        pariatur mollit est velit sunt. Elit tempor adipisicing proident nostrud
        laborum Lorem ullamco. Officia ea in pariatur ullamco adipisicing sunt
        nostrud magna proident nostrud. Ullamco cupidatat laborum commodo aliqua
        sint exercitation minim ullamco ad.
      </p>
    </div>
  </article>
</template>

<style lang="scss">
.about-container {
  img {
    width: 100%;
    border-radius: 50px;
    margin: 30px 0;
  }

  @media screen and (min-width: 768px) {
    p {
      font-size: 18px;
    }

    .inner {
      display: flex;
      align-items: flex-end;
      margin: 0 0 30px;

      p {
        order: 2;
        width: 66%;
        padding: 0 0 20px 30px;
      }

      picture {
        width: 33%;
      }

      img {
        border-radius: 50%;
        margin: 0;
      }
    }
  }
}
</style>
