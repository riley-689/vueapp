<template>
  <div class ="grocery-item" v-bind:class="{'is-complete':grocery.completed}">
    <p>
      <label class="container">
        <input type="checkbox" v-on:change="markComplete" v-bind:checked="grocery.completed">
        <span class = "checkmark"></span>
      </label>
      {{grocery.title}}
      <button @click="$emit('del-grocery', grocery.id)" class="del">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "GroceryItem",
  props: ["grocery"],
  methods: {
    markComplete() {
      this.grocery.completed = !this.grocery.completed;
    }
  }
}
</script>

<style scoped>
  .grocery-item {
    background: #DDDDD4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;

  }

  .is-complete {
    text-decoration: line-through;
  }

  .del {
    background: #3FB984;
    color: #32475E;
    border: none;
    padding: 5px 10px;
    border-radius: 25%;
    cursor: pointer;
    float: right;
  }

  .del:hover {
    background: #3AAD7B;
  }
  .container {
  display: inline-block ;
  position: relative;
  padding-left: 25px;
  margin-bottom: 16px;
  cursor: pointer;
  font-size: 22px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  }

  .container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
  }
  .checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 20px;
  width: 20px;
  border-radius: 25%;
  background-color: #eee;
  }

  /* On mouse-over, add a grey background color */
  .container:hover input ~ .checkmark {
  background-color: #3FB984;
  }

  /* When the checkbox is checked, add a green background */
  .container input:checked ~ .checkmark {
  background-color: #3FB984;
  }


  /* Create the checkmark/indicator (hidden when not checked) */
  .checkmark:after {
  content: "";
  position: absolute;
  display: none;
  }

  /* Show the checkmark when checked */
  .container input:checked ~ .checkmark:after {
  display: inline-block;
  }

  /* Style the checkmark/indicator */
  .container .checkmark:after {
  left: 6px;
  top: 2px;
  width: 5px;
  height: 12px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
  }
</style>
