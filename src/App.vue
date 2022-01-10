<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList v-bind:propsdata="todoItems" v-on:toggleItem="toggleOneItem"></TodoList>
    <TodoFooter v-on:clearAll="clearAllItems"></TodoFooter>
  </div>
</template>


<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'


export default {
  
  data(){
    return{
      todoItems :[],
    
      
    }
  },
  methods:{
  
    toggleOneItem(todoItem ,index) {
      //todoItem.completed = !todoItem.completed;
      this.todoItems[index].completed =!this.todoItems[index].completed;
      localStorage.removeItem(todoItem.item);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    },
    clearAllItems() {
      this.todoItems = [];
      localStorage.clear();
    }
  },
 
  components:{
    //컴포넌트 태그명 : 컴포넌트 내용
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter

  }
 
}
</script>

<style>
body{
  text-align:center;
  background-color: #F6F6F6;

}
input{
  border-style:groove;
  width:200px;
}button{
  border-style: groove;
}
.shadow{
  box-shadow:5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
