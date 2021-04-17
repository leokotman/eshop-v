<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Header :goods='goods'/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import Header from './components/Header';

export default {
  name: 'App',
  components: {
    HelloWorld,
    Header,
  },
  data: function(){
    return {
      goods: ['socks', 'boots'],
    };
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 1rem;
}
</style>
