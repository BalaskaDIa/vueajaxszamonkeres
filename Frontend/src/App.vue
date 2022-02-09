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
  font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #FF5733;
  margin-top: 60px;
}

body
{
  max-width: 1000px;
  margin: auto;
  background-color: #1A5276;
}

#btn_szurke
{
  padding: 10px 20px;
  background-color: #464646;
  color: gainsboro;
}

#btn_narancs
{
  padding: 10px 20px;
  background-color: #FF5733;
  color: gainsboro;
}

input
{
  border: none;
  border-bottom: 2px solid gainsboro;
  background-color: transparent;
  color: wheat;
}
h1
{
  color: wheat;
font-family: century 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
font-size: 50px;
font-weight: bold;
margin-top: 0px;
margin-bottom: 10px
}

</style>
