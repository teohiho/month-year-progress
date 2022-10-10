<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <Progress msg="Creator: @teo"></Progress>
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
  color: #2c3e50;
  margin-top: 60px;
  color: #ebebeb;
  margin: 0 auto;
  width: 50%;
  /* Centering vertically and horizontally  */
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

@media only screen and (max-width: 768px) {
  #app {
    width: 90%;
    transform: translate(-50%, -50%);
    /* top: 70%; */
    left: 50%;
  }
  .progress-year-bar {
    width: 100% !important;
  }
  .progress {
    padding: 0px 15px 0px 15px !important;
  }
  .progress-year-number {
    float: unset !important;
    padding-left: unset !important;
    margin-top: 0.1em;
  }
}

</style>
