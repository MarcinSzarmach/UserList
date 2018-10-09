<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <userList url="https://jsonplaceholder.typicode.com/users"/>
  </div>
</template>

<script>
import userList from './components/userList.vue'

export default {
  name: 'app',
  components: {
    userList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
