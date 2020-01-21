<template>
  <div id="app">
    <Header/>
    <Items v-bind:items="items" v-on:del-item="deleteItem"/>
    <AddWishItem v-on:add-item="addItem"/>
  </div>
</template>

<script>
  import Header from './components/layouts/Header';
  import Items from './components/Items';
  import AddWishItem from './components/AddWishItem';

  export default {
    name: 'app',
    components: {
      AddWishItem,
      Header,
      Items
    },
    data() {
      return {
        items: [
          {
            id: 1,
            title: 'Harry Potter 1',
            description: 'De steen der wijzen',
            img: 'https://s.s-bol.com/imgbase0/imagebase3/large/FC/3/8/8/1/666811883.jpg',
            link: 'https://www.bol.com/nl/p/harry-potter-deel-1-harry-potter-steen-der-wijzen/666811883/?Referrer=ADVNLGOO002008P-G-89205211162-S-851936400856-666811883&gclid=CjwKCAiA35rxBRAWEiwADqB37yjFbUI8lWIVuscHIz-NlnCPPUv0_6IdCMNKzwHA7E1XqeitK83I2BoCeekQAvD_BwE'
          }
        ]
      }
    },
    methods: {
      deleteItem(id) {
        this.items = this.items.filter(item => item.id !== id);
      },
      addItem(newItem) {
        this.items = [...this.items, newItem];
      }
    }
  }
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }
</style>
