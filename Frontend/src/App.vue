<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Statues />
  </div>
</template>

<script>
import Statues from './components/Statues.vue'

export default {
  name: 'App',
  components: {
    Statues
  }
}
</script>

<style>
#app 
{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #FF5733;
  margin-top: 60px;
}

body
{
  max-width: 500px;
  margin: auto;
  background-color: #1A5276;
}
</style>
