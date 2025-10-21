<script>
export default {
    // Add code in appropriate places
    data() {
        return {
            items: ['keyboard', 'mouse', 'iPhone', 'macbook', 'adapter'],
            itemInput: ''
        }

    },
    methods: {
        deleteItem(item) {
            // remove the clicked item from the list
            this.items = this.items.filter(i => i !== item);
        },
        addItem() {
            this.items.push(this.itemInput)
        }
    }
}
</script>

<template>

    <h2>Shopping Cart</h2>
    <div>
        <li v-for="item in items" :key="item">
            {{ item }}
            <button @click="deleteItem(item)">Delete!</button>
        </li>
    </div>

    <input v-model="itemInput"></input><button @click="addItem">Add!</button>
</template>
