<template>
  <li>
    <span v-on:click="toggleDone" v-bind:class="{ strikethrough: todo.done }">
      {{ todo.text }}
    </span>
    <span v-on:click="destroyTodo">
      <a href="#">Destroy</a>
    </span>
  </li>
</template>

<script>
export default {
  name: 'todo-item',
  props: ['todo'],
  methods: {
    toggleDone: function () {
      // can't use arrow functions with 'this'
      this.$emit('toggle-done')
    },
    destroyTodo: function () {
      this.$emit('destroy-todo')
    }
  }
}
</script>

<style>
.strikethrough {
  text-decoration: line-through;
}
</style>
