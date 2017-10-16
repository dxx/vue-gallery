<template>
  <div id="app">
    <gallery />
  </div>
</template>

<script>
import Gallery from "./components/Gallery.vue"

export default {
  name: 'app',
  components: {
    Gallery
  }
}
</script>

<style>
html, body{
  margin: 0;
  padding: 0;
}
html, body, #app{
  width: 100%;
  height: 100%;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
