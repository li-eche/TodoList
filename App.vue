<template>
  <div class="label">
    <table for="">
      <tr>
        <td>
          <MyHeader :receive="receive"></MyHeader>
        </td>
      </tr>
      <tr class="td">
        <MyList
          :todos="todos"
          :checkTodo="checkTodo"
          :deleteTodo="deleteTodo"
        ></MyList>
      </tr>
      <tr>
        <td>
          <MyFooter
            :checkAllTodo="checkAllTodo"
            :todos="todos"
            :clearAllTodo="clearAllTodo"
          ></MyFooter>
        </td>
      </tr>
    </table>
  </div>
</template>
<script>
import MyHeader from "./components/MyHeader.vue";
import MyFooter from "./components/MyFooter.vue";
import MyList from "./components/MyList.vue";
export default {
  name: "app",
  data() {
    return {
      todos: JSON.parse(localStorage.getItem("todos")) || [],
    };
  },
  methods: {
    //添加一个todo
    receive(todoObj) {
      this.todos.unshift(todoObj);
    },
    //勾选or取消勾选一个todo
    checkTodo(id) {
      this.todos.forEach((todo) => {
        if (todo.id == id) todo.done = !todo.done;
      });
    },
    //删除一个todo
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => {
        return todo.id != id;
      });
    },
    //全选or取消全选
    checkAllTodo(done) {
      this.todos.forEach((todo) => {
        todo.done = done;
      });
    },
    //清除所有已完成的todo
    clearAllTodo() {
      this.todos = this.todos.filter((todo) => {
        return !todo.done;
      });
    },
  },
  components: {
    MyFooter,
    MyHeader,
    MyList,
  },
  watch: {
    todos: {
      // 深度监视
      deep: true,
      handler(value) {
        //JSON.stringify 在存储的时候变成字符串类型
        localStorage.setItem("todos", JSON.stringify(value));
      },
    },
  },
};
</script>
<style  >
.label {
  height: 500px;
  width: 550px;
  margin: 0 auto;
  margin-top: 200px;
}
table {
  border: 1px solid rgb(87, 31, 31);
  border-radius: 2%;
  border-spacing: 1px 1.5em;
}
.td {
  border-spacing: 0px 0px;
  border-collapse: collapse;
}
</style>