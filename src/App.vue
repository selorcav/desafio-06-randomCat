<template>
  <div id="app">
    <h1></h1>
    <RandomCat msg="Random Gif Cat"/>
  </div>
</template>

<script>
import RandomCat from './components/RandomCat.vue'

export default {
  name: 'App',
  components: {
    RandomCat
  }
}
</script>

<style>
body{
  background-color: lightseagreen;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
