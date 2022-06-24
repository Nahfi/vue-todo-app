<template>
      <div>
            <div>
                  <form class="x" @submit="addTodo" action="">
                        <input v-model="title" type="text" name="title" placeholder="Add Todo ....">
                        <input type="submit" value="submit" class="btn">
                  </form>

            </div>
      </div>
</template>

<script>
// import uuid from 'uuid';
export default {
      name:'AddTodo',
      data(){
            return{
                  title:''
            }
      },
      methods: {
          addTodo(e){

            const newTodo = {
                  title:this.title,
                  completed:false,
            }
            this.$emit('addTodo',newTodo)
            this.title=' '
            e.preventDefault();
          }
      },
}
</script>
<style scoped>
 form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
  .x{
      margin-top: 5px;
      margin-bottom: 5px;
   }
</style>