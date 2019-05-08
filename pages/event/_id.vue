<template lang="pug">
  h1.title {{ event.title }}
</template>

<script>
import { mapState } from 'vuex'

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
  computed: mapState({
    event: state => state.events.event
  }),
  async fetch({ store, error, params }) {
    try {
      await store.dispatch('events/fetchEvent', params.id)
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
