<template>
  <div id="app">
    <img src="./assets/logo.png">
    <br  />
    <input
      type="text"
      v-model="newTodo"
      @keypress.enter.prevent="addTodo"
    >
    <list
      :todos="todos"
    ></list>
  </div>
</template>

<script>
import eventHub from './event-hub'
import List from './components/List'

export default {
  name: 'app',
  components: {
    List
  },
  data () {
    return {
      newTodo: '',
      todos: [
        { title: 'Buy a milk', completed: false },
        { title: 'Clean the kitchen', completed: false },
        { title: 'Do homework', completed: true }
      ]
    }
  },
  methods: {
    addTodo: function (e) {
      this.todos.push({
        title: this.newTodo,
        completed: false
      })
      this.newTodo = ''
    }
  },
  created () {
    eventHub.$on('toggle', (itemIndex) => {
      this.todos = this.todos.map((todo, idx) => {
        if (itemIndex !== idx) return todo

        todo.completed = !todo.completed
        return todo
      })
    })
    eventHub.$on('remove', (itemIndex) => {
      this.todos.splice(itemIndex, 1)
    })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
