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
        <b-nav-item>
          <nuxt-link to="/home">Home</nuxt-link>
        </b-nav-item>
        <b-nav-item>
          <nuxt-link to="/blog">Blog</nuxt-link>
        </b-nav-item>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</template>

<script>
export default {
  name: "NavComponent",
};
</script>