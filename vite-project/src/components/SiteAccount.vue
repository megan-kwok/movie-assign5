<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
 
const router = useRouter();
 
const username = ref("");
const password = ref("");
const error = ref(false);
 
const login = () => {
  if (username.value === "tmdb" && password.value === "movies") {
    router.push("/purchase");
  } else {
    error.value = true;
  }
};
</script>
 
<template>
  <div class="account-container">
    <h1>Login Here!</h1>
    <form @submit.prevent="login()">
      <input type="text" v-model="username" placeholder="Username" />
      <br>
      <input type="password" v-model="password" placeholder="Password" />
      <br>
      <input type="submit" value="Login" />
    </form>
    <div v-if="error" class="error">
      <p>Incorrect username/password!</p>
    </div>
  </div>
</template>
 
<style scoped>
.account-container > h1 {
  color: rgb(46, 56, 90);
  font-family: 'fredoka one';
  margin-left: 1%;
}
 
.account-container > form {
  margin-left: 1%;
}
</style>