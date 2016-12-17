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
