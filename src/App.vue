<template>
  <div id="app">
    <img src="./assets/logo.png">
    <MyNavbar></MyNavbar>
    <router-view/>
  </div>
</template>

<script>
import MyNavbar from '@/components/MyNavbar'

export default {
  name: 'App',
  components: {MyNavbar}
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
