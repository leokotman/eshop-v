<template>
  <div>
    <h2>Products</h2>
    <ul v-if="noSearchWorked">
      <li v-for="good in goods" v-bind:key="good.id_product">
        <h3>{{ good.product_name }}</h3>
        <span>{{ good.price }}</span>
        <button type="button" @click="addProduct($event)">Add to cart</button>
      </li>
    </ul>
    <ul v-else>
      <li v-for="good in filteredGoods" v-bind:key="good.id_product">
        <h3>{{ good.product_name }}</h3>
        <span>{{ good.price }}</span>
        <button type="button" @click="addProduct($event)">Add to cart</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Products",
  props: {
    noSearchWorked: Boolean,
    goods: {
      type: Array,
    },
    filteredGoods: {
      type: Array,
    },
    goodsInCart: {
      type: Array,
    }
  },
  data(){
    return {
      products: this.goodsInCart,
    }
  },
  methods: {
    addProduct(event) {
      let addedProduct = this._findProductInfo(event);
      console.log(addedProduct);
      this.products.push(addedProduct);
      this.$emit("add-product", this.$data);
    },
    _findProductInfo(event) {
      const btnParent = event.target.parentNode;
      const productTitle = btnParent.querySelector("h3").innerText;
      const productPrice = btnParent.querySelector("span").innerText;
      return {product_name: productTitle, price: productPrice};
    }
  },
};
</script>

<style scoped></style>
