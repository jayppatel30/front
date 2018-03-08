<template>
  <div id="app">
    <h1> Users</h1>
    <user></user>
  </div>
</template>

<script>
import page from './components/user'

export default {
  name: 'App',
  components: {
    user
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
