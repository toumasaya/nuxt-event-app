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

export default {
  components: {
    EventCard
  },
  head() {
    return {
      title: 'Event Lists'
    }
  },
  asyncData({ $axios, error }) {
    return $axios
      .get('http://localhost:4000/events')
      .then(response => {
        return {
          events: response.data
        }
      })
      .catch(e => {
        error({
          statusCode: 503,
          message: 'Unable to fetch events at this time. Please try again.'
        })
      })
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
