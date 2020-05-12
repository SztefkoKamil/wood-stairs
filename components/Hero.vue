<template>
  <div class="hero-container">
    <div class="title-container">
      <span>Welcome to the</span>
      <h1>Wood-Stairs</h1>
      <p>
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Neque
        provident doloribus explicabo natus quia.
      </p>
    </div>
  </div>
</template>

<style lang="scss">
.hero-container {
  background: url('../assets/images/hero-bg.webp') center center;
  background-size: cover;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 120vw;
  max-height: 100vh;
  margin: 50px 0 0;

  .title-container {
    width: 320px;

    span {
      text-align: center;
      display: block;
      font-size: 20px;
      padding: 0 0 10px;
    }

    h1 {
      text-align: center;
      font-size: 42px;
      font-family: 'Permanent Marker';
      letter-spacing: 2px;
    }

    p {
      text-align: center;
      font-size: 14px;
      padding: 20px 15px 0;
    }
  }

  @media screen and (min-width: 768px) {
    & {
      margin: 0;
    }

    .title-container {
      width: 500px;

      span {
        font-size: 28px;
      }

      h1 {
        font-size: 70px;
      }

      p {
        font-size: 20px;
        padding: 20px 20px 0;
      }
    }
  }
}
</style>
