<template>
  <nav class="navbar navbar-expand-lg bg-body-tertiary">
    <div class="container-fluid">
      <h2 class="navbar-brand" to="/">Nuxt SSR</h2>

      <div class="collapse navbar-collapse">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <nuxt-link
              no-prefetch
              exact
              active-class="active"
              class="nav-link"
              to="/"
            >
              Home
            </nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link
              no-prefetch
              active-class="active"
              class="nav-link"
              to="/about"
            >
              About
            </nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link
              no-prefetch
              active-class="active"
              class="nav-link"
              to="/users"
            >
              Users
            </nuxt-link>
          </li>
          <li v-if="!hasToken" class="nav-item">
            <nuxt-link
              no-prefetch
              active-class="active"
              class="nav-link"
              to="/login"
            >
              Login
            </nuxt-link>
          </li>
          <li v-else class="nav-item">
            <a @click.prevent="logout" class="nav-link" href="#"> Logout </a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'Navbar',
  computed: {
    hasToken() {
      return this.$store.getters.hasToken
    },
  },
  methods: {
    logout() {
      this.$store.dispatch('logout')
      this.$router.push('/login')
    },
  },
})
</script>
