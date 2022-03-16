<template>
  <img src="/banner.svg" style="width:100%">
  <img src="/Logo.png" style="margin-bottom: 20px;">
  <authenticator :sign-up-attributes="['email']">
    <template v-slot="{ user, signOut }">
      <h1>Hello {{ user.username }}!</h1>
      <button @click="signOut">Sign Out</button>
    </template>
  </authenticator>
</template>

<script>
import { Authenticator, useAuthenticator } from "@aws-amplify/ui-vue"
const auth = useAuthenticator()
console.log(auth)
import Amplify from 'aws-amplify'
import awsconfig from './aws-exports'

Amplify.configure(awsconfig)

export default {
  name: 'Home',
  components: {
    Authenticator
  }
}
</script>

<style>
body {
  margin: 0px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
