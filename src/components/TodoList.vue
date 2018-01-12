<template>
  <div class="center">
      <p>Completed Tasks: {{todos.filter(todo => {return todo.done == true}).length}}</p>
      <p>Pending Tasks: {{todos.filter(todo => {return todo.done == false}).length}}</p>
      <todo @delete-todo="deleteTodo" 
            @complete-todo="completeTodo"
            v-for="todo in todos" :todo.sync="todo"></todo>
  </div>
</template>

<script type = "text/javascript" >
    /* eslint-disable */
    import Todo from './Todo';

    export default {
        props: ['todos'],
        components: {
            Todo,
        },
        methods: {
            deleteTodo (todo) {
                swal ({
                    title: 'Are you sure?',
                    text: 'This To-Do will be permanently deleted!',
                    type: 'warning',
                    showCancelButton: true,
                    confirmButtonColor: '#DD6B55',
                    confirmButtonText: 'Yes, delete it!',
                    closeOnConfirm: false,
                },
                () => {
                    const todoIndex = this.todos.indexOf(todo);
                    this.todos.splice(todoIndex, 1);
                    swal ('Deleted!', 'Your To-Do has been deleted.', 'success');
                });
            },
            completeTodo (todo) {
                const todoIndex = this.todos.indexOf(todo)
                this.todos[todoIndex].done = true;
                swal ('Success!', 'To-Do completed!', 'success');
            }
        },
    };
</script>

<style>
    .center{
        text-align: center;
        padding-top: 15px;
    }
</style>


