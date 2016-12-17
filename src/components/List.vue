<template>
  <div class="list">
    <item
      v-for="(todo, index) in todos"
      :id="index"
      :title="todo.title"
      :completed="todo.completed"
      @remove="removeItem"
      @toggle="toggleItem"
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
  data () {
    return {
      todos: [
        { title: 'Buy a milk', completed: false },
        { title: 'Clean the kitchen', completed: false },
        { title: 'Do homework', completed: true }
      ]
    }
  },
  methods: {
    removeItem: function (itemIndex) {
      this.todos.splice(itemIndex, 1)
    },
    toggleItem: function (itemIndex) {
      this.todos = this.todos.map((todo, idx) => {
        if (itemIndex !== idx) return todo
        todo.completed = !todo.completed
        return todo
      })
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
