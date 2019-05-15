<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/cart.png">
    <Shoppingcart />
  </div>
</template>

<script>
import Shoppingcart from "./components/Shoppingcart.vue"

export default {
  name: 'app',
  components: {
    Shoppingcart
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
