<template>
  <v-toolbar fixed dark class="cyan" >
    <v-toolbar-title class="mr-4">
      <span class="home" @click="navigateTo({name: 'root'})">
        Tab Tracker
      </span>
    </v-toolbar-title>
    <v-toolbar-items>
      <v-btn flat dark>
        Browse
      </v-btn>
    </v-toolbar-items>
    <v-spacer></v-spacer>
    <v-toolbar-items>
      <v-btn 
        flat
        dark 
        @click="navigateTo({name: 'login'})"
        v-if="!$store.state.isUserLoggedIn" >
        Login
      </v-btn>
      <v-btn 
        flat
        dark
        @click="navigateTo({name: 'register'})"
        v-if="!$store.state.isUserLoggedIn" >
        Sign Up
      </v-btn>
    </v-toolbar-items>
  </v-toolbar>
</template>

<script>
export default {
  name: 'PageHeader',
  data () {
    return {
    }
  },
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.home{
  cursor: pointer;
}
</style>
