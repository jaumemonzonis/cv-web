<template>
  <div id="app">
    <Navbar></Navbar>
    <Home></Home>
    <About></About>
    <Experiencia></Experiencia>
  </div>
</template>

<script>
import Home from "./components/Home";
import Navbar from "./components/Navbar";
import About from "./components/About";
import Experiencia from "./components/Experiencia";


export default {
  components: {
    Home,
    Navbar,
    About,
    Experiencia,
  }
};
</script>

<style lang="scss">
* {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

html {
  height: 100%;
}

body {
  margin: 0;
  padding: 0;
  font-family: "Source Sans Pro", sans-serif;
  font-size: 15px;
  font-weight: 400;
  line-height: 1.75;
  letter-spacing: 1px;
  height: 100%;
}
</style>