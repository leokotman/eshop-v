<template>
    <div class="search">
		<input type="text" class="goods-search" v-model="searchText"/>
		<button class="search-button" type="button" v-on:click="search">Search</button>
	</div>
</template>

<script>
export default {
    name: 'Search',
    props: {
        goods: Array,
    },
    data(){
        return {
            searchText: '',
        }
    },
    methods: {
        search(){
            console.log('filter works');
        },
    },
}
</script>

<style>

</style>