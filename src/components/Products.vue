<template>
  <div>
    <ul v-if="noSearchWorked">
      <li v-for="good in goods" v-bind:key="good.id_product">
        {{ good.product_name }}
        {{ good.price }}
      </li>
    </ul>
    <ul v-else>
      <li v-for="good in filteredGoods" v-bind:key="good.id_product">
        {{ good.product_name }}
        {{ good.price }}
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
      }
  },
};
</script>

<style scoped></style>
