<template>

  <v-layout>
    <v-flex xs6 offset-xs3>
      <div class="white elevation-2">
        <v-toolbar flat dense class="cyan" dark>
          <v-toolbar-title>
            Login
          </v-toolbar-title>
        </v-toolbar>
        <div class="pl-4 pr-4 pt-2 pb-2">
          <form name="tab-tracker-form">
            <v-text-field
              label="Email"
              v-model="email"
              type="email"
              name="email"
            ></v-text-field>
            <br/>
            <v-text-field
              label="Password"
              type = 'password'
              v-model = 'password'
              name= 'password'>
            </v-text-field>
              <br/>
              <div class="error-text" v-html="error"/>
              <v-btn @click = 'login'>Login</v-btn>
          </form>
          </div>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  name: 'Login',
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async login () {
      try {
        const response = await AuthenticationService.login({
          email: this.email,
          password: this.password
        })
        console.log(response)
        this.$store.dispatch('setToken', response.data.token)
        this.$store.dispatch('setUser', response.data.user)
      } catch (err) {
        this.error = err.response.data.error
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error-text{
  color:red
}
</style>
