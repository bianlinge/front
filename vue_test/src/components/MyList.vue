<template>

    <ul class="todo-main">
        <MyItem v-for="todoObj in todos" 
        :key="todoObj.id" 
        :todo="todoObj" 
        :handleCheck="handleCheck"
        :deleteTodoById="deleteTodoById"
    
        />
    </ul>

</template>

<script>
import MyItem from './MyItem.vue'

export default {
    name: "MyList",
    props:["todos","handleCheck","deleteTodoById"],
    components: { MyItem },
   
}
</script>

<style>
/*main*/
.todo-main {
    margin-left: 0px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding: 0px;
}
</style>