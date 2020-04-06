<template>
  <div>
    <form @submit="addItem">
      <input type="text" v-model="title" name="title" placeholder="Add grocery items...">
      <input type="submit" value="Add Item" class="btn">
    </form>
  </div>
</template>

<script>
import {v4 as uuidv4} from 'uuid';
export default {
  name: "AddItem",
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addItem(e) {
      e.preventDefault();
      const newItem = {
        id: uuidv4(),
        title: this.title,
        completed: false
      }
      this.$emit('add-item', newItem);
      this.title = '';
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
  }

  input[type="text"] {
    flex: 10;
    padding: 5px;
    background-color: #DDDDD4;
    border: beige;
    border-bottom: #ccc;
    border-bottom-style: solid;
  }

  input[type="submit"] {
    flex: 1;
  }
</style>
