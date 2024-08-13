<template>
  <section>
    <h1>Users Page</h1>

    <ul>
      <li v-for="user of users" :key="user.id">
        <a href="#" @click.prevent="openUser(user.id)"> {{ user.name }} </a>
      </li>
    </ul>
  </section>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  // VUEX SSR подход. Работает аналогично asyncData
  async fetch({ store }) {
    if (store.getters['users/users'].length === 0) {
      await store.dispatch('users/fetch')
    }
  },

  // SSR подход, т.к. работаем мы сейчас на сервере и обращаемся к контексту получаемому на вход, а не с this!
  // Но работает только для первой загрузки! Ввиду nuxt-link дальше отрабатывает как SPA - обычный fetch запрос
  // async asyncData({ $axios }) {
  //   const users = await $axios.$get(
  //     'https://jsonplaceholder.typicode.com/users'
  //   )

  //   return { users }
  // },

  // data: () => ({
  //   users: [] as { id: number; name: string }[],
  // }),

  computed: {
    users() {
      return this.$store.getters['users/users']
    },
  },

  // не SSR подход, т.к. данные получаем постфактум
  // async mounted() {
  //   this.users = await this.$axios.$get(
  //     'https://jsonplaceholder.typicode.com/users'
  //   )
  // },
  methods: {
    openUser(userID: number) {
      this.$router.push(`/users/${userID}`)
    },
  },
})
</script>
