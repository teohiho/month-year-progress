<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <Progress msg="Welcome to Your Vue.js App"></Progress>
</template>

<script>
import Progress from './components/Progress.vue'

export default {
  name: 'App',
  components: {
    Progress
  }
}
</script>

<style>
body {
  background-color: #1d1d1d;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
  color: #ebebeb;
  margin: 0 auto;
  width: 700px;
  /* Centering vertically and horizontally  */
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  
}

</style>
