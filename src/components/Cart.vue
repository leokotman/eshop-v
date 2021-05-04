<template>
<div>
    <h2>Cart</h2>
    <p>{{cartGoods}}</p>
</div>
</template>

<script>
export default {
    name: "Cart",
    props: {
        cartGoods: Array,
    }
}
</script>

<style scoped>

</style>
