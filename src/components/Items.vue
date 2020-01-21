<template>
    <div class="items">
        <div v-bind:key="item.id" v-for="item in items">
            <WishListItem v-bind:item="item" v-on:del-item="$emit('del-item', item.id)" />
        </div>
    </div>
</template>

<script>
    import WishListItem from "./WishListItem.vue";

    export default {
        name: "Items",
        components: {
            WishListItem
        },
        props: ["items"]
    }
</script>

<style scoped>
    .items {
        display: grid;
        grid-template-columns: 1fr 1fr;
    }
</style>