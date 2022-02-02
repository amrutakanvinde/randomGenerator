<template>
  <div id="app">
    <CardGenerator msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import CardGenerator from './components/CardGenerator.vue'

export default {
  name: 'App',
  components: {
    CardGenerator
  }
}
</script>

<style>
#app {
  /* font-family: Avenir, Helvetica, Arial, sans-serif; */
  font-family: 'Roboto Slab', serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

html, body{
  margin: 0;
  padding: 0;
  background-color: #CCCCCC;
}

</style>
