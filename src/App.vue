<template>
  <SignUp></SignUp>
</template>

<script>

import SignUp from "./components/Signup.vue"

export default {
  
  components: {
    SignUp:SignUp,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body{
  background-color: #eee;
  margin: 0;
}
</style>
