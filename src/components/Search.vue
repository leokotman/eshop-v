<template>
    <div class="search">
		<input type="text" class="goods-search" v-model="searchText" value="searchText"/>
		<button class="search-button" type="button" @click="search(searchText)" :value="searchText">Search</button>
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
        search(searchText){
            console.log('search from Search works');
            this.$emit('search-content', searchText);
        },
    },
}
</script>
