<template>
    <div>
      <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completetodo" v-for="todo in filterTodos" v-bind:todo="todo" :key="todo.id"></todo>
    </div>
</template>

<script type = "text/javascript" >
import todo from './Todo'
export default {
  name: 'todo-list',
  props: ['filterTodos', 'todos'],
  components: {
    todo
  },
  methods: {
    deleteTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos.splice(todoIndex, 1)
    },
    completetodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos[todoIndex].completed = !this.todos[todoIndex].completed
    }
  }
}
</script>
<style>
</style>
