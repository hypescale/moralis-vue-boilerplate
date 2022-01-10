<template>
  <div>{{user}}</div>
  <button v-if="!isAuthenticated" @click="logIn">logIn</button>
  <button v-if="isAuthenticated" @click="logOut">LogOut</button>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue'
import Moralis from 'moralis'

const serverUrl = process.env.VUE_APP_MORALIS_SERVER_URL
const appId =  process.env.VUE_APP_MORALIS_APPLICATION_ID
Moralis.start({ serverUrl, appId })

let user = ref({})

onMounted(() => {
  user.value = Moralis.User.current();
})

const isAuthenticated = computed(() => user.value)

const logIn = async () => {
  if (!isAuthenticated.value) {
    user.value = await Moralis.authenticate({ signingMessage: "Log in using Moralis" })
      .then((user) => {
        console.log("logged in user:", user);
        console.log(user.get("ethAddress"));
        return user
      })
      .catch((error) => {
        console.log(error);
      });
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
