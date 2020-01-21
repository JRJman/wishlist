<template>
    <div class="wishList-item" v-bind:class="{'is-complete':item.completed}">
        <div>
            <div class="item__title">{{item.title}}</div>
            <div class="item__img"><img v-bind:src="item.img" v-bind:alt="item.title"></div>
            <div class="item__description">{{item.description}} <a v-bind:href="item.link">Link naar item</a></div>
            <button @click="$emit('del-item', item.id)" class="del">x</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "WishListItem",
        props: ['item'],
        methods: {
            markComplete() {
                this.item.completed = !this.item.completed;
            }
        }
    }
</script>

<style scoped>
    .wishList-item {
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .item__title {
        text-align: center;
        font-size: 36px;
    }

    .item__img img{
        display: block;
        margin: 0 auto;
        height: 300px;
    }

    .item__description {
        display: block;
        margin: 0 auto;
        width: 70%;

    }

    .is-complete {
        text-decoration: line-through;
    }

    .del {
        position: relative;
        top: -200px;
        font-size: 60px;
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 5px 20px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>