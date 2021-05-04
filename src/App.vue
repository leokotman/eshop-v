<template>
  <div id="app">
    <Header
      :goods="goods"
      @header-search="filterContent"
      @open-cart="openCart"
    />
    <Cart v-show="cartOpened" :cart-goods="goodsInCart"/>
    <Products
      :no-search-worked="noSearchWorked"
      :goods="goods"
      :filtered-goods="filteredGoods"
      :goods-in-cart="goodsInCart"
      @add-product="addToCart"
    />
  </div>
</template>

<script>
import Header from "./components/Header";
import Cart from "./components/Cart";
import Products from "./components/Products";

export default {
  name: "App",
  components: {
    Header,
    Cart,
    Products,
  },
  data: function() {
    return {
      goods: [],
      filteredGoods: [],
      goodsInCart: [],
      noSearchWorked: true,
      cartOpened: false,
    };
  },
  methods: {
    filterContent(searchText) {
      console.log(searchText);
      let searchedGoods = this.goods.filter((good) => {
        return good.product_name.includes(searchText);
      });
      this.filteredGoods = searchedGoods;
      this.noSearchWorked = false;
    },
    fetchGoods() {
      fetch(
        "https://raw.githubusercontent.com/GeekBrainsTutorial/online-store-api/master/responses/catalogData.json"
      )
        .then((response) => response.json())
        .then((data) => (this.goods = data));
    },
    openCart() {
      if (this.cartOpened) {
        return (this.cartOpened = false);
      } else {
        return (this.cartOpened = true);
      }
    },
    addToCart() {
      console.log(this.goodsInCart);
      console.log("goods pushed in goodsInCart");
    },
  },
  mounted() {
    this.fetchGoods();
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 1rem;
}
</style>
