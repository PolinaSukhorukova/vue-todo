<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos :todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from '../components/Todos.vue'
import AddTodo from '../components/AddTodo.vue'
import axios from 'axios'

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Home',
  components: {
    Todos,
    AddTodo,
  }, 
  data () {
    return {
      todos: []
    }
  }, 
  methods: {
    deleteTodo (id) {
      axios.delete(`https://mate.academy/students-api/todos/${id}`)
        .then(() => this.todos = this.todos.filter(todo => todo.id !== id))
        .catch(err => console.log(err))
    },
    addTodo (newTodo) {
      const { title, completed } = newTodo
      axios.post('https://mate.academy/students-api/todos', {
        userId: 607,
        title,
        completed
      })
        .then(res => this.todos.push(res.data))
        .catch(err => console.log(err))
    }
  },
  created () {
    axios.get('https://mate.academy/students-api/todos?userId=607')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err))
  }
}
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
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
