<template>
  <div>
      <div class="div">
          <HeaderLayoutVues/>
          <div class="todo-form">
          <AddTodoVue  v-on:addTodo="addTodo" />
          </div>
          <ToDoVue v-bind:todos="todos" v-on:deleteTodo = "deleteTodo"/>
      </div>
  </div>
</template>

<script>

import ToDoVue from './components/ToDo.vue'
import HeaderLayoutVues from './components/layouts/HeaderLayout.vue'
import AddTodoVue from './components/AddTodo.vue'
import axios from 'axios';
export default {
  title: 'App',
  components:{
    ToDoVue,
    HeaderLayoutVues,
    AddTodoVue

  },
  data(){
    return{
      todos:[
       
      ]
    }
  },
  methods:{
    deleteTodo(id){
       axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`).
       then(res => this.todos.forEach((value,index)=>{
        
        if(id == value.id){
          this.todos.splice(index,1)
        }
        console.log(res)
       }))
        .catch(e=>console.log(e))

    },
    addTodo(newTodo){
      let {title,completed} = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos/',{title,completed}).then(res=>  this.todos = [...this.todos,res.data])
 
      
    },

  },
  created() {
      axios.get('https://jsonplaceholder.typicode.com/todos/?_limit=10').then(res => this.todos = [...res.data]).catch(e=>console.log(e))
    },

}
</script>

<style>
.todo-form{
  margin: 0 auto;
  width: 40%;
 }
 *{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body{
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
