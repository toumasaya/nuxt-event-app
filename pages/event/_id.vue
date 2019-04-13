<template lang="pug">
  h1.title Event no.{{ id }}
</template>

<script>
export default {
  head() {
    return {
      title: 'Event no.' + this.id,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'This is your event no.' + this.id
        }
      ]
    }
  },
  computed: {
    id() {
      return this.$route.params.id
    }
  }
}
</script>

<style></style>
