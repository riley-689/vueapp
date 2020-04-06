<template>
  <div id="app">
    <Header />
    <addItem v-on:add-item="addItem"/>
    <Grocery v-bind:grocery="grocery" v-on:del-grocery="deleteGrocery" />
  </div>
</template>

<script>
import Header from './components/Header'
import Grocery from './components/Grocery'
import AddItem from './components/AddItem'
export default {
  name: 'App',
  components: {
    Header,
    Grocery,
    AddItem
  },
  data() {
    return {
      grocery: [
        {
          id: 1,
          title: "Eggs",
          completed: true
        },
        {
          id: 2,
          title: "Milk",
          completed: false
        },
        {
          id: 3,
          title: "Bread",
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteGrocery(id) {
      this.grocery = this.grocery.filter(grocery => grocery.id != id);
    },
    addItem(newItem) {
      this.grocery = [...this.grocery, newItem];
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
  font-family: sans-serif;
  font-weight: bold;
  font-size: 1.25em;
  line-height: 2.0;
  color: #32475E;
  background-color: #32475E;
}

.btn {
  display: inline-block;
  border: none;
  background: #3FB984;
  color: #fff;
  padding: 15px 5px;
  cursor: pointer;
}

.btn:hover {
  background: #3AAD7B;
}
</style>
