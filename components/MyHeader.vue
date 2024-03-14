<template>
  <div>
    <input class="input" v-model="title" placeholder="请输入你的任务名称，按回车键确认" @keyup.enter ="add"/>
  </div>
</template>

<script>
import {nanoid} from "nanoid"
export default {
  name:"MyHeader",
  props:["receive"],
  data(){
    return{
      title:''
    }
  },
  methods:{
    add(e){
      //校验数据
      if(!this.title)return alert("输入不能为空")
      //儿子给老子传东西
      const todoObj= {id:nanoid(),title:e.target.value,done:false}
      //通知App组件去添加一个todo对象
      this.receive(todoObj)
      //清空输入
      this.title =""
    }
  }
};
</script>

<style>
.input{
    height: 30px;
    width: 542px;
}
</style>