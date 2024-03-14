<template>
  <tr>
    <td>
      <div class="list">
        <label for="">
          <input type="checkbox" :checked="todoobj.done" @click="handleCheck(todoobj.id)"/>
          <!-- 不建议用，因为done是包裹在todoobj当中的，如果不包裹在当中就会报错，以为props中的属性不能改 -->
          <!-- <input type="checkbox" v-model="todoobj.done" v-model是双向数据绑定/> -->
          <span>{{ todoobj.title }}</span>
        </label>
        <button @click="handleDelete(todoobj.id)">删除</button>
      </div>
    </td>
  </tr>
</template>

<script>
export default {
  name: "MyItem",
  //声明接收todo对象
  props: ["todoobj","checkTodo","deleteTodo"],
  methods:{
    //
    handleCheck(id){
      //通知App组件将对应的todo对象的done值取反
      this.checkTodo(id)
    },
    // handleDelete(id){
    //   if(confirm('确定删除吗？')){
    //     console.log(id)
    //   }
    // }
    handleDelete(id){
      this.deleteTodo(id)
    }
  }
};
</script>

<style scoped >
div{
  width: 549px;
  height: 35px;
}
button {
  display: none;
  float: right;
  width: 50px;
  height: 35px;
  background-color: red;
  border-radius: 10%;
}
div:hover {
  background-color:#ddd;

}
.list:hover button{
  display: block;
}
</style>