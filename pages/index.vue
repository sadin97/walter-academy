<template>
  <section class="container">
    <div>
      <Navigation></Navigation>
    </div>
  </section>
</template>

<script>
import Navigation from '~/components/Navigation.vue'

export default {
  components: {
    Navigation
  }
}
</script>

<style lang="scss">
@import "../assets/mixins";
@import "../assets/variables";
@import url('https://fonts.googleapis.com/css?family=Roboto');

html, body {
  margin: 0;
  font-family: 'Roboto' !important;

  @media (max-width: 425px) {
    font-size: 1em;
  }
}

body {
  font-family: 'Roboto' !important;
}

.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
