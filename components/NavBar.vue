<template lang="pug">
  .nav-wrapper
    nav.navbar.container
      .navbar-brand
        nuxt-link.navbar-item.has-text-primary(to="/") Nuxt Events
      .navbar-menu
        nuxt-link.navbar-item(to="/") Events
        nuxt-link.navbar-item(to="/create") Create
      .navbar-end
        .navbar-item
          .buttons
            nuxt-link(class="button is-primary" to="/"): strong Sign up
            nuxt-link(class="button is-light" to="/") Sign in
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.nav-wrapper {
  background: white;
}

.navbar-brand {
  font-family: 'Baloo', cursive;
  font-size: 1.5rem;
}
</style>
