<template>
  <ul>
    <!-- 遍历 -->
    <MyItem v-for="todoobj in todos" 
    :key="todoobj.id" 
    :todoobj="todoobj" 
    :checkTodo="checkTodo"
    :deleteTodo="deleteTodo"></MyItem>
  </ul> 
</template>

<script>
import MyItem from "./MyItem.vue";
export default {
  name: "MyList",
  components: {
    MyItem,
  },
  props:["todos","checkTodo","deleteTodo"]
};
</script>
<style scoped >
tr {
  border: 1px solid rgb(215, 213, 213);
  border-collapse: collapse;
  border-spacing: 0px 0px;
}
ul{
  list-style:none;
  margin:0px;
  padding:0px;
}
</style>
