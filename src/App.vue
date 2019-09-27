<template>
  <div id="app">
    <CircleCross/>
  </div>
</template>

<script>
import CircleCross from "./components/CircleCross.vue";

export default {
  name: 'App',
  components: {
      CircleCross
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
