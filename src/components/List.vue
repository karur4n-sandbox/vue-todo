<template>
  <div class="list">
    <item
      v-for="(todo, index) in todos"
      :id="index"
      :title="todo.title"
      :completed="todo.completed"
    ></item>
  </div>
</template>

<script>
import Item from './Item'

export default {
  name: 'list',
  components: {
    Item
  },
  props: {
    hub: true,
    todos: {
      type: Array,
      required: true
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
