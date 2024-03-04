<template>
<!-- Input fields for adding a new item -->
<div class="container">
    <div class="row">
        <div class="col-md-8">
            <input type="text" class="form-control" v-model="newItemText" placeholder="Enter new item">
        </div>
        <div class="col-md-4">
            <button @click="addItem" class="btn btn-primary btn-block">Add Item</button>
        </div>
    </div>

    <!-- List to display items -->
    <ul class="list-group mt-3">
        <li class="list-group-item" v-for="(item, index) in items" :key="index">
            {{ item }}
            <button @click="editItem(index)" class="btn btn-sm btn-secondary ml-2">Edit</button>
            <button @click="deleteItem(index)" class="btn btn-sm btn-danger ml-2">Delete</button>
        </li>
    </ul>

    <!-- Modal for editing an item -->
    <div v-if="editingIndex !== null">
        <input type="text" v-model="editedItemText">
        <button @click="saveEdit">Save</button>
        <button @click="cancelEdit">Cancel</button>
    </div>
</div>
</template>

<script>
export default {
    name: 'Students',
    data() {
        return {
            items: ['item-1', 'item-2', 'item-3'],
            newItemText: '',
            editingIndex: null,
            editedItemText: ''
        }
    },
    methods: {
        addItem() {
            this.items.push(this.newItemText);
            this.newItemText = '';
            console.log(this.items);
        },
        deleteItem(index) {
            this.items.splice(index, 1);
        },
        editItem(index) {
            this.editingIndex = index;
            this.editedItemText = this.items[index];           
        },
        saveEdit() {
            this.items[this.editingIndex] = this.editedItemText;
            this.editingIndex = null;
        },
        cancelEdit() {
            this.editingIndex = null;
        }
    }
        }

       
    
</script>
