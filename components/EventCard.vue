<template lang="pug">
  .column
    .card
      .card-header
        p.card-header-title {{ event.title }}
      .card-content
        p @{{ event.time }} on {{ parsedDate }}
        p {{ event.attendees.length }} attending
      footer.card-footer
        nuxt-link.card-footer-item(:to="'/event/' + event.id") Check Event

</template>

<script>
export default {
  name: 'EventCard',
  props: {
    event: Object
  },
  computed: {
    parsedDate() {
      const eventDate = new Date(this.event.date)
      return eventDate.toDateString()
    }
  }
}
</script>

<style></style>
