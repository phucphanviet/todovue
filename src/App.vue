<template>
  <div>
    <todos v-bind:todos="todos" v-bind:newtodo="newtodo" v-bind:visibility="visibility"></todos>
  </div>
</template>

<script>
import Todos from './components/Todos'
export default {
  name: 'App',
  data () {
    return {
      todos: [
        {
          id: 0,
          title: 'todo',
          completed: false
        }
      ],
      newtodo: '',
      visibility: 'All'
    }
  },
  components: {
    Todos
  }
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 40%;
}
</style>
