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
      <input type="text" id="text" v-model="username" placeholder="Username" />
      <br>
      <input type="password" id="password" v-model="password" placeholder="Password" />
      <br>
      <input type="submit" id="login" value="Login" />
      <p>Forgot Password?</p>
    </form>
    <div v-if="error" class="error">
      <p>Incorrect username/password!</p>
    </div>
  </div>
</template>
 
<style scoped>
.account-container {
  background: rgba(51, 61, 119, 0.548);
  border-radius: 1rem;
  width: 35rem;
  height: 35rem;
  margin-top: 10%;
  margin-left: 30%;
  margin-bottom: 10%;
}

.account-container>h1 {
  color: rgb(35, 39, 85);
  font-family: 'fredoka one';
  text-align: center;
  font-size: 45px;
  padding: 2rem;
}

.account-container>form {
  margin-left: 12%;
  padding: 2%;
}

.account-container>form>#text {
  padding: 2%;
  border-radius: 1rem;
  border-color: rgb(123, 128, 168);
  font-family: 'lato';
  margin-bottom: 3%;
  width: 25rem;
}

.account-container>form>#password {
  padding: 2%;
  border-radius: 1rem;
  border-color: rgb(123, 128, 168);
  font-family: 'lato';
  margin-bottom: 3%;
  width: 25rem;
}

.account-container>form>#login {
  padding: 1%;
  background: rgb(123, 128, 168);
  border-radius: 1rem;
  border-color: rgb(123, 128, 168);
  font-family: 'lato';
}
.account-container>form>p {
  display: flex;
  margin-top: 2%;
}
.error {
  margin-left: 13.5%;
}
</style>