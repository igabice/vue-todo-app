<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
   <create-todo v-on:create-todo='createTodo'></create-todo>
    <todo-list v-bind:todos="todos"></todo-list>
    
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld'
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo'

export default {
  name: 'App',
  components: {
    TodoList,
    CreateTodo
  },
  data() {
    return {
      todos: [
        {
          title: "Todo A",
          project: 'Project A',
          done: false,
        },
        {
          title: "Todo B",
          project: 'Project B',
          done: false,
        },
        {
          title: "Todo C",
          project: 'Project C',
          done: true,
        },
        {
          title: "Todo D",
          project: 'Project D',
          done: false,
        }
      ]
    }
  },
  methods: {
    createTodo(todo){
      this.todos.push({
        title: todo.title,
        project: todo.project,
        done: false
      });
    }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
