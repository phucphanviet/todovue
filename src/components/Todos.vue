<template>
  <div class="container" id='app'>
        <h1 class="is-size-1 has-text-centered has-text-weight-semibold has-text-grey">Todos</h1>
        <div class="has-background-white " id="todo-app">
            <div class="panel" id="input-todo">
                <div class="panel-block" id="padding-input">
                    <input-todo  v-bind:todos="todos" v-bind:newtodo="newtodo" v-on:add-todo="addTodo"></input-todo>
                </div>
            </div>
            <div class="panel-block is-marginless tabs is-centered has-text-centered" >
              <ul id="border-none">
                <li v-bind:class="{'is-active': visibility == 'All'}">
                  <a v-on:click="filterAll()" id="border-none">
                    <span>ALL</span>
                  </a>
                </li>
                <li v-bind:class="{'is-active': visibility == 'Active'}">
                  <a v-on:click="filterActive()" id="border-none">
                    <span>ACTIVE</span>
                  </a>
                </li>
                <li v-bind:class="{'is-active': visibility == 'completed'}">
                  <a v-on:click="filtercompleted()" id="border-none">
                    <span>COMPLETED</span>
                  </a>
                </li>
              </ul>
            </div>
            <todo-list v-bind:filterTodos="filterTodos" v-bind:todos="todos"></todo-list>
        </div>
  </div>
</template>

<script>
import InputTodo from './InputTodo'
import TodoList from './TodoList'
export default {
  name: 'todos',
  props: ['todos', 'newtodo', 'visibility'],
  components: {
    InputTodo,
    TodoList
  },
  computed: {
    filterTodos () {
      if (this.visibility === 'All') {
        return this.todos
      } else {
        if (this.visibility === 'Active') {
          return this.todos.filter(todo => {
            return todo.completed === false
          })
        }
      }
      return this.todos.filter(todo => {
        return todo.completed === true
      })
    }
  },
  methods: {
    addTodo: function (value) {
      if (!value) {
        return
      }
      this.todos.push({
        id: this.todos.length,
        title: value,
        completed: false
      })
      value = ''
    },
    filterAll: function () {
      this.visibility = 'All'
    },
    filterActive: function () {
      this.visibility = 'Active'
    },
    filtercompleted: function () {
      this.visibility = 'completed'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#todo-app {
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2), 0 25px 50px 0 rgba(0, 0, 0, 0.1);
}
#input-todo {
  margin-bottom: 0px;
}
#padding-input {
  padding-top: 14px;
  padding-bottom: 14px;
}
#border-none {
  border: none !important;
}
</style>
