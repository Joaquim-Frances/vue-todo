<template>
  <div>
    <div id="header"></div>
    <div id="main-container">
      <h2>Tareas Pendientes</h2>
      <todo-add v-on:addTodo="addTodo" />
      <Todos v-bind:todoslist="copyTodos" v-on:deleteTodo="deleteTodo"/>
    </div>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
// import Search from './components/Search';
import Todos from './components/Todos';
import TodoAdd from './components/TodoAdd';


export default {
  name: 'App',
  components: {
    Todos, TodoAdd
  },
  methods: {
    deleteTodo(id){
      this.todos= this.todos.filter(todo => todo.id != id);
      this.copyTodos = [...this.todos];
    },
    addTodo(todo){
      this.todos.push(todo);
      this.copyTodos = [...this.todos];
    },
  },
  data(){
    return{
      todos: [
        {
          id: 0,
          title: 'Sorra pel cactus',
          completed: false,
        },
        {
          id: 1,
          title: 'Reparar Bicicleta',
          completed: false,
        },
        {
          id: 2,
          title: 'Apendre Vue',
          completed: false,
        },
        {
          id: 3,
          title: 'Acabar tutorial',
          completed: true,
        }
      ],
      copyTodos: []
    }
},
created(){
  this.copyTodos = [...this.todos];
}
}
</script>

<style>
*{
    box-sizing: border-box;
  }
  body{
    font-family: Arial, Helvetica, sans-serif;
    font-size: 1.5em;
    padding: 0;
    margin: 0;
  }
  #main-container{
    border: solid 1px #ccc;
    width: 600px;
    margin: 100px auto;
  }
  #header{
    background: black;
    padding: 10px;
  }
  h2{
    padding: 0 10px;
  }
</style>
