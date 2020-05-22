<template>
  <footer class="footer">
    <div class="inner-footer">
      <span>Wood-Stairs 2020 &copy; All Rights Reserved</span>
      <span
        >Design & production:
        <a href="mailto:contact@kamilsztefko.pl"
          >contact@kamilsztefko.pl</a
        ></span
      >
    </div>
  </footer>
</template>

<style lang="scss">
.footer {
  margin: 70px 0 0;
  font-size: 14px;
  background: var(--bg-secondary);
  padding: 30px 0;

  .inner-footer {
    max-width: 840px;
    margin: 0 auto;
    display: flex;
    flex-flow: column;
    align-items: center;
    padding: 0 30px;

    span:first-child {
      margin: 0 0 10px;
    }

    a {
      color: currentColor;
    }
  }

  @media screen and (min-width: 700px) {
    .inner-footer {
      flex-flow: row;
      justify-content: space-between;

      span:first-child {
        margin: 0;
      }
    }
  }

  @media screen and (min-width: 900px) {
    .inner-footer {
      padding: 0;
    }
  }
}
</style>
