<template>
  <div id="app">
    <Navbar /> 
    <Main /> 
    <Filtro />
    <Footer />
  </div>
</template>

<script>
import Filtro from './components/Filtro.vue'
import Navbar from './components/navbar.vue'
import Footer from './components/Footer.vue'
import Main from './components/main.vue'

export default {
  name: 'App',
  components: {
    Filtro,
    Navbar,
    Footer,
    Main,
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
  background-image: linear-gradient(
      to bottom,
      rgba(208, 226, 231, 0),
      rgba(241, 246, 248, 0.952)
    ),
    url("./assets/Casa1.jpg")
    ;
    background-repeat: no-repeat;
    background-attachment: fixed;
}
</style>
