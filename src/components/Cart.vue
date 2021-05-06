<template>
<div>
    <h2>Cart</h2>
    <ul>
        <li v-for="(good, index) in cartGoods" :key="index">
            <span>{{good.product_name}}</span>
            <span>{{good.price}}</span>
            <span>{{good.quantity}}</span>
        </li>
    </ul>
    <!-- <p>{{cartGoods}}</p> -->
</div>
</template>

<script>
export default {
    name: "Cart",
    props: {
        cartGoods: Array,
    },
    methods: {

    },
    beforeUpdate() {
        for (let i = 0; i < this.cartGoods.length; i++) {
                let duplicateGoods = this.cartGoods.filter(good => good.product_name == this.cartGoods[i].product_name);
                if (!duplicateGoods) {
                    continue;
                } else {
                    this.cartGoods[i].quantity = duplicateGoods.length;
                }
        }
    }
}
</script>

<style scoped>

</style>
