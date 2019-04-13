<template lang="pug">
  h1.title {{ event.title }}
</template>

<script>
export default {
  head() {
    return {
      title: 'Event: ' + this.event.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'This is your event no.' + this.event.title
        }
      ]
    }
  },
  async asyncData({ $axios, error, params }) {
    try {
      const { data } = await $axios.get(
        'http://localhost:4000/events/' + params.id
      )
      return {
        event: data
      }
    } catch (e) {
      error({
        statusCode: 503,
        message: `Unable to fetch event no.${
          params.id
        } at this time. Please try again.`
      })
    }
  }
}
</script>

<style></style>
