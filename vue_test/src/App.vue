<template>

  <div class="todo-container">
    <div class="todo-wrap">
      <MyHeader :addTodo="addTodo"/>
      <MyList :todos="todos" :handleCheck="handleCheck" :deleteTodoById="deleteTodoById"/>
      <MyFooter  :todos="todos" :checkAll="checkAll"    :clearAll="clearAll"/>
    </div>
  </div>


</template>

<script>
import MyHeader from "./components/MyHeader.vue"
import MyList from "./components/MyList.vue"
import MyFooter from "./components/MyFooter.vue"
export default {
  name: "App",
  components: { MyHeader, MyList, MyFooter },
  data() {
        return {
          todos: [
                { id: "001", title: "吃饭", done: true },
                { id: "002", title: "睡觉", done: false },
                { id: "003", title: "打豆豆", done: true }]
        }
    },
  methods: {
    //添加一個todo
    addTodo(todo){
      this.todos.unshift(todo)
      console.log("我是APP组件",todo)
    },
    //勾選一個todo
    handleCheck(id){
      this.todos.forEach((todo)=>{
        if(todo.id===id) todo.done = !todo.done
      })
    },
    deleteTodoById(id){
    this.todos= this.todos.filter((todo)=>{
        return todo.id !==id
      })
    },
    checkAll(value){
      this.todos.forEach((todo)=>todo.done = value)
    },
    clearAll(){
      this.todos= this.todos.filter((todo)=>{
        return !todo.done
      })
    }
  },
};
</script>

<style>
    /*base*/
    body {
    background: #fff;
}
.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

</style>