<template>
    <div class="search">
		<input type="text" class="goods-search" />
		<button class="search-button" type="button" v-on:click="filter" >Search</button>
	</div>
</template>

<script>
export default {
    name: 'Search',
    props: {
        goods: Array,
    },
    methods: {
        filter(){
            console.log('filter worked');
        },
    }
}
</script>

<style>

</style>