<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <CompoundInterest/>
  </div>
</template>

<script>
import CompoundInterest from './components/CompoundInterest.vue'

export default {
  name: 'App',
  components: {
    CompoundInterest
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
</style>
