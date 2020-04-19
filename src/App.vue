<template>
  <div id="app">
    <Calculator />
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  name: 'App',
  components: {
    Calculator
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: rgb(185,136,196);
  background: -moz-radial-gradient(circle, rgba(185,136,196,1) 0%, rgba(124,76,176,1) 100%);
  background: -webkit-radial-gradient(circle, rgba(185,136,196,1) 0%, rgba(124,76,176,1) 100%);
  background: radial-gradient(circle, rgba(185,136,196,1) 0%, rgba(124,76,176,1) 100%);
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr="#b988c4",endColorstr="#7c4cb0",GradientType=1);
  height: 100vh;
}

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>
