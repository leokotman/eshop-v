<template>
<section class="tobuy_list">
    <h2> {{ title }} </h2>
    <span v-if="errorMsg">{{errorMsg}}</span>
    <label for="title">Item title</label>
    <input v-model="item.title" type="text" name="title" required>
    <label for="desc">Item description</label>
    <textarea v-model="item.description" name="desc" cols="30" rows="3"></textarea>
    <button @click="addItem">Add new item</button>
    <ul>
        <li v-for="(item, index) in items" :key="index">
            <h3> {{item.title}}</h3>
            <p>{{item.description}}</p>
            <span>{{item.date}}</span>
        </li>
    </ul>
</section>
</template>

<script>
export default {
    name: "ToBuy",
    data() {
        return {
            title: "To-buy list",
            item: {
                title: "",
                description: "",
                date: ""
            },
            items: [],
            errorMsg: null,
        }
    },
    methods: {
        addItem() {
            let {title, description} = this.item;
            if (title === "") {
                this.errorMsg = "Title can't be blank!";
                return false;
            }
            this.items.push({
               title: title,
               description: description,
               date: new Date(Date.now()).toLocaleString(),
            });
            this.item.title = "";
            this.item.description = "";
            this.errorMsg = null;
        },
    }
}
</script>

<style scoped>
.tobuy_list {
    display: flex;
    flex-direction: column;
    box-sizing: border-box;
    width: 60vw;
    margin: 0 auto;
}
input {
}
textarea {
    resize: vertical;
}
</style>
