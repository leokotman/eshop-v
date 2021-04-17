<template>
    <nav class="menu-links">
        <span><a href="#">Home</a></span>
        <span><a href="#">Products</a></span>
        <span><a href="#">About us</a></span>
        <span><a href="#">Contacts</a></span>        
    </nav>
</template>

<script>
export default {
    name: 'Menu'
}
</script>

<style scoped>
.menu-links{
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
}
</style>
