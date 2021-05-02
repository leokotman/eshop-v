<template>
  <div id="app">
    <Header :goods='goods' @header-search="filteredContent"/>
    <ul v-if="noSearchWorked">
      <li v-for="good in goods" v-bind:key="good.id_product"> {{good.product_name}} {{good.price}}</li>
    </ul>
    <ul v-else>
      <li v-for="good in filteredGoods" v-bind:key="good.id_product"> {{ good.product_name }} {{good.price}} </li>
    </ul>

  </div>
</template>

<script>
import Header from './components/Header';

export default {
  name: 'App',
  components: {
    Header,
  },
  data: function(){
    return {
      goods: [],
      filteredGoods: [],
      noSearchWorked: true,
    };
  },
  methods: {
    filteredContent(searchText){
      console.log(searchText);
      let searchedGoods = this.goods.filter(good => {
        return good.product_name.includes(searchText);
      });
      this.filteredGoods = searchedGoods;
      this.noSearchWorked = false;
    },
    fetchGoods() {
      fetch('https://raw.githubusercontent.com/GeekBrainsTutorial/online-store-api/master/responses/catalogData.json')
        .then(response => response.json())
        .then(data => (this.goods = data));
    },
  },
  mounted () {
    this.fetchGoods();
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 1rem;
}
</style>
