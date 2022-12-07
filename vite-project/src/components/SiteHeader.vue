<script setup>
import { useRouter } from 'vue-router';
 
const router = useRouter();
 
const login = () => {
  router.push("/login");
};
</script>
 
<template>
  <div class="header-container">
  <div class="header">
    <h1>Movie Log</h1>
  </div>
    <form @submit.prevent="login()">
      <button @click="login" class="login">Login</button>
    </form>
  </div>
</template>
 
<style scoped>
.header-container {
  justify-content: space-between;
  display: flex;
  background-color: rgb(46, 56, 90);
  border-radius: 1rem;
}
.header {
  color: white;
  font-family: 'fredoka one';
  font-size: 1.5rem;
  margin-left: 3%;
}
.login {
  float: right;
  color: white;
  background-color: rgb(123, 128, 168);
  border-color: white;
  border-radius: 1rem;
  font-size: 1.5rem;
  margin-top: 55%;
  margin-right: 55%;
}
</style>