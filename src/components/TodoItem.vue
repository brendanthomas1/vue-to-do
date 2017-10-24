<template>
  <li v-on:click="toggleDone" v-bind:class="{ strikethrough: todo.done }">
    {{ todo.text }}
  </li>
</template>

<script>
export default {
  name: 'todo-item',
  props: ['todo'],
  methods: {
    toggleDone: function () {
      this.$emit('toggle-done')
    }
  }
}
</script>

<style>
.strikethrough {
  text-decoration: line-through;
}
</style>
