<template>
  <div id="app">
    <Header :goods='goods' @header-search="filterContent" @open-cart="openCart" />
    <Cart v-show="cartOpened"/>
    <ul v-if="noSearchWorked">
      <li v-for="good in goods" v-bind:key="good.id_product">
         {{ good.product_name}}
         {{good.price}}</li>
    </ul>
    <ul v-else>
      <li v-for="good in filteredGoods" v-bind:key="good.id_product">
        {{ good.product_name }}
        {{good.price}} </li>
    </ul>
  </div>
</template>

<script>
import Header from './components/Header';
import Cart from './components/Cart';

export default {
  name: 'App',
  components: {
    Header,
    Cart,
  },
  data: function(){
    return {
      goods: [],
      filteredGoods: [],
      noSearchWorked: true,
      cartOpened: false,
    };
  },
  methods: {
    filterContent(searchText){
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
    openCart() {
      if (this.cartOpened){
        return this.cartOpened = false;
      } else {
        return this.cartOpened = true;
      }
    }
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
