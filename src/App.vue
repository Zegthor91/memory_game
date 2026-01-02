<script setup>
import Home from './views/Home.vue'
</script>

<template>
  <div id="app">
    <Home />
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  overflow-x: hidden;
}

#app {
  width: 100%;
  min-height: 100vh;
}
</style>
