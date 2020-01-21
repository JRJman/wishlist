<template>
    <div>
        <form @submit="addItem">
            <input type="text" v-model="title" name="title" placeholder="Add item...">
            <input type="text" v-model="description" name="description" placeholder="Add Description">
            <input type="text" v-model="img" name="img" placeholder="Add Image link of item">
            <input type="text" v-model="link" name="link" placeholder="Add Link to item">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
    import uuid from 'uuid';
    export default {
        name: 'AddItem',
        data() {
            return {
                title: '',
                description: '',
                img: '',
                link: ''
            }
        },
        methods: {
            addItem(e) {
                e.preventDefault();
                const newItem = {
                    id: uuid.v4(),
                    title: this.title,
                    description: this.description,
                    img: this.img,
                    link: this.link,
                    completed: false
                }
                //Send up to parent
                this.$emit('add-item', newItem);

                this.title = '';
                this.description = '';
                this.img = '';
                this.link = '';
            }
        }
    }
</script>

<style scoped>
    form {
        display: flex;
    }

    input[type='text'] {
        flex: 10;
        padding: 5px;
    }

    input[type='submit'] {
        flex: 2;
    }
</style>