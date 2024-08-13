<template>
  <section>
    <h1>{{ user.name }}</h1>

    <hr />
    <h3>{{ user.email }}</h3>
  </section>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  validate({ params }) {
    return /^\d+$/.test(params.id)
  },
  async asyncData({ $axios, params }) {
    const user = await $axios.$get(
      'http://jsonplaceholder.typicode.com/users/' + params.id
    )

    return { user }
  },
  computed: {
    userId() {
      return this.$route.params.id
    },
  },
})
</script>
