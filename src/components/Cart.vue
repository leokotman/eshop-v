<template>
<div>
    <h2>Cart</h2>
    <ul>
        <li v-for="(good, index) in updatedQuantityGoods" :key="index">
            <span>{{good.product_name}}</span>
            <span>{{good.price}}</span>
            <span>{{good.quantity}}</span>
        </li>
        <p>{{cartGoods}}</p>
    </ul>
</div>
</template>

<script>
export default {
    name: "Cart",
    props: {
        cartGoods: Array,
    },
    data() {
        return {
            updatedQuantityGoods: [],
        }
    },
    methods: {
        updateQuantity() {
            this.updatedQuantityGoods = this.removeDuplicates(this.cartGoods, this.cartGoods.product_name);
            console.log('filter worked');
            console.log(this.updatedQuantityGoods);
            return this.updatedQuantityGoods;
        },
        removeDuplicates(arr, key) {
            return [...new Map(arr.map(item => [item[key], item])).values()];
        },
    },
    beforeUpdate() {
        console.log('before update stuff');
        for (let i = 0; i < this.cartGoods.length; i++) {
                let duplicateGoods = this.cartGoods.filter(good => good.product_name == this.cartGoods[i].product_name);
                if (!duplicateGoods) {
                    continue;
                } else {
                    this.cartGoods[i].quantity = duplicateGoods.length;
                }
        }
        this.updateQuantity();
    }
}
</script>

<style scoped>
ul {
    width: 60%;
    margin: 0 auto;
}
ul li {
    display: flex;
    justify-content:space-evenly;
}
</style>
