<template lang="pug">
  section.section
    .container
      b-icon(icon="alert-circle" size="is-large")
      h1.title {{ message }}
      p(v-if="statusCode === 404")
        nuxt-link(to="/") Return to homepage
</template>

<script>
export default {
  props: {
    error: {
      type: Object,
      default: null
    }
  },
  head() {
    return {
      title: this.message
    }
  },
  computed: {
    statusCode() {
      return (this.error && this.error.statusCode) || 500
    },
    message() {
      return this.error.message
    }
  }
}
</script>

<style lang="scss" scoped>
.container {
  text-align: center;
}
</style>
