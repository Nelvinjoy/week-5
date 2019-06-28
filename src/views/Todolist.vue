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
import axios from "axios";


export default {
  data: function(){
    return{
      todos:'',
      todoList:[]
    }
  },
components: {
  todo, todoForm
},
methods:{
  appDeleteTodo(index){
    this.todoList.splice(index, 1);
    axios.put("https://joy00027-vue-and-axios.firebaseio.com/data.json", this.todoList);
  },
addTodo(todo){
  this.todoList.push(todo);
  axios.put("https://joy00027-vue-and-axios.firebaseio.com/data.json", this.todoList).then(response => {
console.log(response);
    console.log('your data was saved status :' + response.status);
  }).catch(error => {
    console.log(error);
  });
}

},
created(){
  console.log("app is created");
  axios.get("https://joy00027-vue-and-axios.firebaseio.com/data.json").then(response =>{
    console.log(response);
    console.log(response.data);
    if(response.data) this.todoList = response.data;
  }).catch(error =>{
    console.log("there was an error in getting your data "+ error.response);
  })
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
