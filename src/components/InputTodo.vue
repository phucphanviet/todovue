<template>
    <input v-model="newtodo" v-on:keyup.enter="addTodo(newtodo)" class="input is-rounded" type="text" placeholder="New Todo">
</template>

<script>
export default {
  name: 'input-todo',
  props: ['todos', 'newtodo'],
  methods: {
    addTodo (value) {
      this.$emit('add-todo', value)
    }
  }
}
</script>
