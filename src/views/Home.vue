<template>
<div id="home">
  <AddTodo @add-todo="addTodo"/>
  <Todos v-bind:todos="todos" @del-todo="deleteTodo" @mark-complete="markComplete"/>
</div>
</template>

<script>
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    // Header,  
    Todos, 
    AddTodo,
  },
  data() {
    return {
      todos: [ ]
    }
  },
  methods: {
    deleteTodo(id) {
      // this.todos = this.todos.filter(todo => todo.id != id);
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(this.todos = this.todos.filter(todo => todo.id != id))
      .catch(error => console.log(error))
    },

    markComplete(todo) {
      todo.completed = !todo.completed;
    },

    addTodo(newTodo) {
      // pick out the title from newTodo
      const { title, completed } = newTodo;
      //post request 
      axios.post('https://jsonplaceholder.typicode.com/todos', {
      title,    // use destructured title n completed from "pick out title" section to post
      completed
      })
      .then(res => this.todos = [...this.todos, res.data])
      .catch(error => console.log(error));
    }
  },
  
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(res => this.todos = res.data)
    .catch(error => console.log(error))
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 8px;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;  
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
</style>
