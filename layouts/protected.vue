<template>
  <div class="container">
    <div>
      <nuxt-link to="/">Home</nuxt-link>
      <a href='#' @click="signout">Logout</a>
    </div>
    <div>
      <nuxt/>
    </div>
  </div>
</template>

<script>
  import { mapActions } from 'vuex'

  export default {
    middleware: 'authenticated',
    methods: {
      ...mapActions('modules/user', [ 'logout' ]),
      async signout () {
        await this.logout()
        this.$router.push('/')

        // this.logout().then(() => {
        //   this.$router.push('/')
        // }).catch((error) => {
        //   console.log(error.message)
        // })
      }
    }
  }
</script>

<style>
  a {
    padding: 5px;
  }
</style>
