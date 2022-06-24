<template>
      <div>
         <div v-for="todo in todos" :key="todo.id">
             <ToDoListVue v-bind:todo="todo" v-on:deleteTodo="$emit('deleteTodo',todo.id)"/>
         </div>
      </div>
</template>

<script>
import ToDoListVue from './ToDoList.vue'
export default {
      name:"ToDo",
      props:{
            todos:Array
      },

      components:{
        ToDoListVue
      },
      data(){
            return({
                 
            })
      }
}
</script>

<style scoped>
</style>