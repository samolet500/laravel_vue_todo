<template>
    <div class="todoListContainer">
        <div class="heading">
            <h2 id="title">Todo List</h2>
            <add-item-form @reloadList="getList()"/>
        </div>

        <list-view
            :items="items"
            @reloadList="getList()"
        />
    </div>
</template>

<script>
import AddItemForm from "./addItemForm";
import ListView from "./listView";

export default {
    name: 'App',

    components: {ListView, AddItemForm},

    data() {
        return {
            items: []
        }
    },

    methods: {
        getList() {
            axios.get('api/items')
            .then( response => {
                this.items = response.data
            })
            .catch( error => {
                console.log(error)
            })
        }
    },

    created() {
        this.getList();
    }
}
</script>

<style scoped>
    .todoListContainer {
        width: 350px;
        margin: auto;
    }

    .heading {
        padding: 10px;
        background: #e6e6e6;
    }

    #title {
        text-align: center;
    }
</style>
