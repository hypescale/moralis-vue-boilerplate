<template>
  <div>{{user}}</div>
  <button v-if="!user" @click="logIn">logIn</button>
  <button v-if="user" @click="logOut">LogOut</button>
</template>

<script setup>
import { ref } from 'vue'
import Moralis from 'moralis'

Moralis.initialize(process.env.VUE_APP_MORALIS_APPLICATION_ID);
Moralis.serverURL = process.env.VUE_APP_MORALIS_SERVER_URL;
const user = ref(null)

const logIn = async () => {
  user.value = Moralis.User.current();
  if (!user.value) {
    user.value = await Moralis.authenticate();
  }
  console.log("logged in user:", user.value);
}

const logOut = async () => {
  await Moralis.User.logOut();
  user.value = null
  console.log("logged out");
}
</script>

<style scoped>
</style>
