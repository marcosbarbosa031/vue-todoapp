<template>
  <div id="app">
    <h1 class="ui dividing centered header">
      <i class="add to calendar icon"></i>
      Todo List</h1>
    <div class='ui three column centered grid'>
      <div class='column'>
        <TodoList v-bind:todos="todos"/>
        <CreateTodo @create-todo="createTodo"/>
      </div>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';

export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo,
  },
  data () {
    return {
      todos: []
    }
  },
  methods: {
    createTodo (newTodo) {
      this.todos.push(newTodo)
      swal ('Success!', 'To-Do created!', 'success')
    }
  }
};
</script>

<style>
/* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
#app h1{
  padding-top: 15px;
}
</style>
