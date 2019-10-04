<template>
<v-app>

  <v-app-bar app>
    Welcome To My Todo App <v-icon dark>mdi-wrench</v-icon>
  </v-app-bar>

  <!-- Sizes your content based upon application components -->
  <v-content>

          <div class='column'>
        <todo-list v-bind:todos="todos"></todo-list>
        <create-todo v-on:create-todo="createTodo"></create-todo>
      </div>

    <!-- Provides the application the proper gutter -->
    <v-container fluid>
    </v-container>
  </v-content>

  <v-footer app>
    TODO APP
  </v-footer>
</v-app>
</template>
<script>
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';

export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo,
  },
  data() {
    return {
      todos: [{
        title: 'Todo 1',
        project: 'Project A',
        done: false,
      }, {
        title: 'Todo 2',
        project: 'Project B',
        done: true,
      }, {
        title: 'Todo 3',
        project: 'Project C',
        done: false,
      }, {
        title: 'Todo 4',
        project: 'Project D',
        done: false,
      }],
    };
  },
  methods: {
    createTodo(newTodo) {
      this.todos.push(newTodo);
      alert('To-Do created!');
    },
  },
};
</script>
