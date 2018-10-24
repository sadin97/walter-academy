<template>
  <div>
    <div class="header">
      <Navigation/>
    </div>
    <div class="main">
      <nuxt/>
    </div>
  </div>
</template>

<script>
import Navigation from '~/components/Navigation.vue'

export default {
  components: {
    Navigation
  }
}
</script>

<style lang="scss" scoped>
  @import "../assets/mixins";

  .layout {
    @include create-main-grid(3)
  }

  .header {
    grid-area: header;
  }
  .main {
    height: calc(100vh - 80px);
    margin-top: 80px;
    grid-area: main;
  }
  .space {
    grid-area: space;
  }
  .footer {
    grid-area: footer;
  }

</style>
