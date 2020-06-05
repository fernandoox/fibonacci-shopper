<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" id="image" />
    <h3>Shopper test: Fibonacci</h3>
    <h5>By: Luis Fernando Fz</h5>
    <Fibonacci />
  </div>
</template>

<script>
import Fibonacci from "./components/Fibonacci.vue";
import "./styles/theme.scss";
export default {
  name: "App",
  components: {
    Fibonacci,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#image {
  width: 10%;
}
</style>
