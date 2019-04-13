<template lang="pug">
  .main-content
    NavBar
    section.section
      .container
        nuxt
</template>

<script>
import NavBar from '~/components/NavBar.vue'

export default {
  components: {
    NavBar
  }
}
</script>

<style lang="scss">
body {
  background: hsl(0, 0%, 96%);
}
</style>
