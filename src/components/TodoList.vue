<template>
  <div id='foo'>
    <h1>To Do</h1>

    <div id='form'>
      <input id='new-todo-input' />
      <button v-on:click="addTodo">Add</button>
    </div>

    <ul>
      <todo-item v-for='todo in todos' v-bind:todo='todo'
      v-on:toggle-done="toggleDone(todo)">
      </todo-item>
    </ul>
  </div>
</template>

<script>
import TodoItem from './TodoItem'

let todos = [{text: 'Make spaghetti', done: false}]

export default {
  name: 'todo-list',
  data () {
    return {
      todos: todos,
      msg: 'Todos'
    }
  },
  components: { TodoItem },

  methods: {
    addTodo: () => {
      let input = document.getElementById('new-todo-input')
      todos.push({text: input.value, done: false})
      input.value = ''
    },

    toggleDone: (todo) => (todo.done = !todo.done)
  }
}
</script>

<style>
#foo {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

li {
  cursor: pointer;
}
</style>
