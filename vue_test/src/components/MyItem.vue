<template>
  <li>
    <label>
      <input
        type="checkbox"
        :checked="this.todo.done"
        @change="addTodo(todo.id)"
      />
      <span>{{ this.todo.title }}</span>
    </label>

    <button class="btn btn-danger" @click="deleteTodo(todo.id)">删除</button>
  </li>
</template>

<script>
export default {
  name: "MyItem",
  props: ["todo", "handleCheck", "deleteTodoById"],
  methods: {
    addTodo(id) {
      this.handleCheck(id);
    },
    deleteTodo(id) {
		if(confirm("确认删除吗？"))
      this.deleteTodoById(id);
    },
  },
};
</script>

<style scoped>
/*item*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  background-color: red;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}

li:hover {
  background-color: #ddd;
}

li:hover button {
  display: block;
}
</style>