<template>
    <div class="search">
		<input type="text" class="goods-search" v-model="searchText" value="searchText" @input="search(searchText)" />
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
            this.$emit('search-content', searchText);
        },
    },
}
</script>
