<template>
  <b-navbar
    toggleable="lg"
    type="light"
    variant="light"
    class="p-3 border-bottom"
    fixed="top"
  >
    <nuxt-link class="navbar-brand" to="/">mason</nuxt-link>
    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav class="mr-auto">
          <nuxt-link class="nav-item" to="/home">Home</nuxt-link>
          <nuxt-link class="nav-item" to="/blog">Blog</nuxt-link>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</template>

<script>
export default {
  name: "NavComponent",
};
</script>