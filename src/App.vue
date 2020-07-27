<template>
  <div id="app">
    <Header title="Calculator created with Vue.js" />
    <img alt="Vue logo" src="./assets/logo.png" />
    <Calculator />
    <Footer copyright="Lucian Iernye 2020" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Calculator from "./components/Calculator";
import Footer from "./components/Footer";

export default {
  name: "App",
  components: {
    Header,
    Calculator,
    Footer,
  },
};
</script>

<style>
/* body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
} */

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

img {
  position: relative;
  top: -50px;
  width: 100px;
}
</style>
