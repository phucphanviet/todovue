<template>
   <div class="is-large" >
                <div class="panel-block colomns" id="border-top">
                    <input class="column is-1" type="checkbox" v-on:click="completetodo(todo)" :checked="todo.completed">
                    <div class="column is-10" v-bind:class="{'is-completed': todo.completed==true}"> {{todo.title}}</div>
                    <a class="delete column" v-on:click="deletetodo(todo)"></a>
                </div>
    </div>
</template>
<script type="text/javascript">
export default {
  name: 'todo',
  props: ['todo'],
  methods: {
    deletetodo (value) {
      this.$emit('delete-todo', value)
    },
    completetodo (value) {
      this.$emit('complete-todo', value)
    }
  }
}
</script>

<style scoped>
.is-completed {
  color: hsl(0, 5%, 81%) !important;
  text-decoration: line-through;
}
#border-top {
  border-top: none;
}
input:focus{
  outline: 0px;
}
</style>
