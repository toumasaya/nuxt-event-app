<template lang="pug">
  div
    h1.title Events
    .columns
      EventCard(
        v-for="(event, index) in events"
        :key="index"
        :event="event"
        :data-index="index")
</template>

<script>
import EventCard from '~/components/EventCard.vue'
import { mapState } from 'vuex'

export default {
  components: {
    EventCard
  },
  head() {
    return {
      title: 'Event Lists'
    }
  },
  computed: mapState({
    events: state => state.events.events
  }),
  async fetch({ store, error }) {
    try {
      await store.dispatch('events/fetchEvents')
    } catch (e) {
      error({
        statusCode: 503,
        message: 'Unable to fetch events at this time. Please try again.'
      })
    }
  }
}
</script>

<style lang="scss"></style>
