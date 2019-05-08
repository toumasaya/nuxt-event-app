<template lang="pug">
  h1.title {{ event.title }}
</template>

<script>
import EventService from '@/services/EventService.js'

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
  async asyncData({ error, params }) {
    try {
      const { data } = await EventService.getEvent(params.id)
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
