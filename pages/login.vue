<template>
  <section>
    <div class="alert alert-danger mb-3" v-if="$route.query.message">
      Need login first
    </div>
    <form action="" @submit.prevent="onSubmit">
      <div class="form-group">
        <h1>Login page</h1>
        <input type="text" class="form-control" />
        <p>
          <nuxt-link to="/">To home page</nuxt-link>
        </p>
        <button class="btn btn-primary">Login</button>
      </div>
    </form>
  </section>
</template>

<!-- <script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  layout: 'empty',
})
</script> -->

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  layout: 'empty',
  methods: {
    onSubmit() {
      this.$store.dispatch('login')
      this.$router.push('/')
    },
  },
})
</script>

<style scoped>
form {
  width: 500px;
  margin: 0 auto;
}
</style>
