<template>
  <v-layout column>
    <v-flex xs offset-xs3>
      <div class="white elevation-2">
        <v-toolbar flat dense class="cyan" dark>
          <v-toolbar-title>Register</v-toolbar-title>
        </v-toolbar>
        <div class="pl-4 pr-4 pt-2 pb-2">
          <v-text-field
            label="Email"
            v-model="email"
          ></v-text-field>
          <v-text-field
            label="Password"
            v-model="password"
          ></v-text-field>
          <br>
          <div class="error" v-html="error"></div>
          <v-btn
          dark
          class="cyan"
          @click="register">Register</v-btn>
        </div>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  name: 'Register',
  data () {
    return {
      'email': '',
      'password': '',
      'error': null
    }
  },
  methods: {
    async register () {
      try {
        await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {
  color: red;
}
</style>
