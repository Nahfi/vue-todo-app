<template>
      <div>
            <div class="todo-item" v-bind:class="{'is-complete':todo.completed }">
                  <h3 @click="changeStatus" >
                      {{ todo.title }}
                    <button class="del" @click="$emit('deleteTodo',this.data.id)">X</button>
                  </h3>
            </div>
      </div>
</template>
<script>
export default {
      name:"ToDoList",
      props:{
            todo:Object
      },
      data(){
            return{
                  data:this.todo
            }
      },
      methods:{
            changeStatus(){
                  this.data.completed = !this.data.completed
            },
      }
      
}
</script>

<style scoped>
.todo-item {
    margin: 0 auto;
    cursor: pointer;
    width: 40%;
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }
  .is-complete {
    text-decoration: line-through;
  }
  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>