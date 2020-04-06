<template>
  <div>
    <div v-bind:key="grocery.id" v-for="grocery in grocery">
      <GroceryItem v-bind:grocery="grocery" v-on:del-grocery="$emit('del-grocery',grocery.id)" />
    </div>
  </div>
</template>


<script>
import GroceryItem from './GroceryItem.vue';
export default {
  name: "Grocery",
  components: {
    GroceryItem
  },
  props: ["grocery"]
}

</script>

<style scoped>

</style>
