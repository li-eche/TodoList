<template>
  <div v-show="total">
    <label for="">
      <input type="checkbox" v-model="isAll" />
    </label>
    <span>
      <span>已完成{{ doneTotal }}</span
      >/全部{{ todos.length }}
    </span>
    <button @click="clear()">清除已完成</button>
  </div>
</template>

<script>

export default {
  name: "MyFooter",
  props: ["todos", "checkAllTodo", "clearAllTodo"],
  computed: {
    total() {
      return this.todos.length;
    },
    doneTotal() {
      let i = 0;
      this.todos.forEach((todo) => {
        if (todo.done) i++;
      });
      return i;
    },
 

    //reduce 实现
    // doneTotal(){
    //   this.todos.reduce((pre,current)=> pre + (current.done?1:0),0)
    // }

    //修改得用get 与 set
    isAll: {
      get() {
        return this.doneTotal === this.total && this.total > 0;
      },
    },
    set(value) {
      return this.checkAllTodo(value);
    },
  },
  methods:{
    clear(){
      this.clearAllTodo()
    },
  }

};
</script>

<style>
button {
  float: right;
  width: 100px;
  height: 35px;
  background-color: red;
  border-radius: 10%;
}
</style>