<template>
  <div id="test">
    <Navbar />
    <main class="container">
      <nuxt />
    </main>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Navbar from '~/components/Navbar.vue'

export default Vue.extend({
  components: {
    Navbar,
  },
})
</script>
