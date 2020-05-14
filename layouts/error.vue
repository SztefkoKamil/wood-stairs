<template>
  <article class="error-container">
    <h1>{{ error.message }}</h1>
    <h2>Error status: {{ error.statusCode }}</h2>
    <n-link to="/">go back to Home Page</n-link>
  </article>
</template>

<script>
export default {
  props: ['error'],
  layout: '404'
}
</script>

<style lang="scss">
.error-container {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-flow: column;
  align-items: center;
  justify-content: center;
  padding: 20px;

  h1 {
    font-family: 'Volkhov';
    font-size: 40px;
    font-weight: 400;
    text-align: center;
    line-height: 130%;
  }

  h2 {
    font-size: 30px;
    font-weight: 400;
    margin: 20px 0 50px;
    text-align: center;
  }

  a {
    text-decoration: none;
    font-size: 20px;
    color: var(--color-primary);
    padding: 20px 30px;
    border: 1px solid var(--primary);
    background-color: var(--bg-secondary);
  }
}
</style>
