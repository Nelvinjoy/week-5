<template>

  <div>

    <h1>To-Do list</h1>
    <todoForm @newTodo="addTodo">
<h2 slot="title">Add a todo</h2>
<p slot="desc">thiss will add the todo</p>

    </todoForm>

<todo :todos="todoList" @removeTodo="appDeleteTodo" />
  </div>
</template>
<script>
import todo from "@/components/Todo.vue";
import todoForm from "@/components/todoform.vue";


export default {
  data: function(){
    return{
      todos:'',
      todoList:["walk the dog", "go for a ride", "go Crazy"]
    }
  },
components: {
  todo, todoForm
},
methods:{
  appDeleteTodo(index){
    this.todoList.splice(index, 1);
  },
addTodo(todo){
  this.todoList.push(todo);
}

}
}
</script>
<style>
ul{
  list-style: none;
  width:50%;
  margin: 0 auto;
}
ul li{
  border-bottom: 1px solid #acacac;
  padding: 10px 0;
  
}

</style>
