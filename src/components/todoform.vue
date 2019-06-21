<template>
  <div>
    <slot name="title"></slot>
    <form @submit.prevent="addTodo">
      <input type="text" v-model="todos">
<slot name="desc"></slot>
<slot>Default slot, placeholder content</slot>
    </form>
  </div>
</template>

<script>
export default {
  data(){
    return{
      todos:""

    }
  },
  methods:{
    addTodo(){
      if(this.todos.length){
        this.$emit('newTodo',this.todos);
        this.todos = "";
      }
    }
  }
};
</script>

<style lang="css" scoped>
input{
  min-width: 200px;
  padding: 10px 20px;
  font-size: 1.5rem;
}
</style>
