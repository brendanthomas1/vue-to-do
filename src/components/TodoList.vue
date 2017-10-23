<template>
  <div id='foo'>
    <h1>To Do</h1>

    <div id='form'>
      <input id='new-todo-input' />
      <button v-on:click="addTodo">Add</button>
    </div>

    <ul>
      <li v-for='todo in todos'
          v-on:click="toggleDone(todo)"
          v-bind:style="{ textDecoration: (todo.done ? 'line-through' : '')}"
      >
        {{ todo.text }}
      </li>
    </ul>
  </div>
</template>

<script>
let todos = [{text: 'Make spaghetti', done: false}]

export default {
  name: 'TodoList',
  data () {
    return {
      todos: todos,
      msg: 'Todos'
    }
  },

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
