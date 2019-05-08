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
import EventService from '@/services/EventService.js'

export default {
  components: {
    EventCard
  },
  head() {
    return {
      title: 'Event Lists'
    }
  },
  async asyncData({ error }) {
    try {
      const { data } = await EventService.getEvents()
      // const response = await $axios.get('http://localhost:4000/events')
      return {
        events: data
        // events: response.data
      }
    } catch (e) {
      error({
        statusCode: 503,
        message: 'Unable to fetch events at this time. Please try again.'
      })
    }
  }
  // asyncData(context) {
  //   return context.$axios.get('http://localhost:4000/events').then(response => {
  //     return {
  //       events: response.data
  //     }
  //   })
  // }
}
</script>

<style lang="scss"></style>
