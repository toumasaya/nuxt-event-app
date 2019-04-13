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
  },
  head() {
    return {
      titleTemplate: '%s - Nuxt Events',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Real world events!'
        }
      ]
    }
  }
}
</script>

<style lang="scss">
body {
  background: hsl(0, 0%, 96%);
}
</style>
