<template>
  <div>{{ user }}</div>
  <button v-if="!isAuthenticated" @click="logIn">logIn</button>
  <button v-else @click="logOut">LogOut</button>
</template>

<script lang="ts" setup>
import { ref, onMounted, computed } from "vue";
import Moralis from "moralis";

const serverUrl = import.meta.env.VITE_MORALIS_SERVER_URL;
const appId = import.meta.env.VITE_MORALIS_APPLICATION_ID;
Moralis.start({ serverUrl, appId });

const user = ref<Moralis.User<Moralis.Attributes> | void | null>(null);
const isAuthenticated = computed<boolean>(() => user.value !== null);

onMounted(() => {
  if(!isAuthenticated.value) {
    user.value = Moralis.User.current();
  }
});

const logIn = async () => {
  if (!isAuthenticated.value) {
    user.value = await Moralis.authenticate({
      signingMessage: "Log in using Moralis",
    })
      .then((user) => user)
      .catch((error) => {
        console.error(error);
      });
  }
  console.log("logged in user:", user.value);
};

const logOut = async () => {
  await Moralis.User.logOut();
  user.value = null;
  console.log("logged out");
};
</script>

<style scoped></style>
