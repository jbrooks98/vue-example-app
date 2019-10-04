<template>
  <div>
    <p class="tasks">Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p class="tasks">Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <div v-for="(todo, index) in todos">
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" :todo.sync="todos[index]"></todo>
    </div>

  </div>
</template>

<script>
import Todo from './Todo';
export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(todo) {
        const todoIndex = this.todos.indexOf(todo);
        this.todos.splice(todoIndex, 1);
        alert('Your To-Do has been deleted.');
    },
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
      alert('To-Do completed!');
    },
  },
};
</script>

<style scoped>
p.tasks {
  text-align: center;
}
</style>