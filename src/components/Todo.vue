<template>
<ul>
  <li v-for="(todo, index) in todos" :key="index" @click="todoDone(index)">
    {{todo}}
  </li>
</ul>
</template>

<script>
export default {
props:{
  todos: {
    type: Array,
    required: true
  }
},
methods: {
  todoDone(index) {
    console.log(index);
    // $emit emits ab event fromthe child component to the parent
    this.$emit("removeTodo", index);//two parameteres 1 what is to be done 2 the value
  }
}
}
</script>

<style lang="css" scoped>
li{
  font-weight: bold;
}
</style>
