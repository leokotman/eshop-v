<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Header :goods='goods' @header-search="filteredContent"/>
    <ul v-if="noSearchWorked">
      <li v-for="good in goods" v-bind:key="good.id"> {{good.name}}</li>
    </ul>
    <ul v-else>
      <li v-for="good in filteredGoods" v-bind:key="good.id"> {{ good.name }} </li>
    </ul>

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
      goods: [
        {
          id: 0,
          name: 'socks'
        },
        {
          id: 1,
          name: 'boots'
        },
      ],
      filteredGoods: [],
      noSearchWorked: true,
    };
  },
  methods: {
    filteredContent(searchText){
      console.log(searchText);
      let searchedGoods = this.goods.filter(good => {
        return good.name.includes(searchText);
      });
      this.filteredGoods = searchedGoods;
      this.noSearchWorked = false;
    }
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
