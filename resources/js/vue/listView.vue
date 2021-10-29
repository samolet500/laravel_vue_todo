<template>
    <div>
        <div v-for="(item, index) in items" :key="index">
            <list-item
                :item="item"
                class="item"
                @itemChange="$emit('reloadList')"
            />
        </div>
    </div>
</template>

<script>
import ListItem from "./listItem";

export default {
    name: 'ListView',

    components: {ListItem},

    props: ['items']
}
</script>

<style scoped>
.item {
    background: #e6e6e6;
    padding: 10px;
    margin-top: 5px;
}
</style>
