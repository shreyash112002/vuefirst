<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <TicTacToe />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import TicTacToe from './components/TicTacToe.vue';

export default {
  name: 'app',
  components: {
    // HelloWorld
    TicTacToe
  }
}
</script>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>
