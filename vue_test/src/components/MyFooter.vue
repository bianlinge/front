<template>
  <div class="todo-footer" v-show="todos.length > 0">
    <label>
      <!-- <input type="checkbox" :checked="isAll" @click="checkTodoAll" /> -->
      <input type="checkbox" v-model="isAll" />
    </label>
    <span>
      <span>已完成{{ dealTotal }}</span> / 全部{{ total }}
    </span>
    <button class="btn btn-danger" @click="clearAllTodos">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: "MyFooter",
  props: ["todos", "checkAll","clearAll"],
  computed: {
    total() {
      return this.todos.length;
    },
    dealTotal() {
      const t = this.todos.reduce((pre, todo) => {
        return pre + (todo.done ? 1 : 0);
      }, 0);
      return t;
    },
    // isAll() {
    //   return this.total === this.dealTotal && this.total > 0;
    // },

    isAll: {
      get() {
        return this.total === this.dealTotal && this.total > 0;
      },
      set(value) {
        console.log(value);
        this.checkAll(value);
      },
    },
  },
  methods: {
    // checkTodoAll() {
    //   console.log("@",this.isAll);
    //   this.checkAll(!this.isAll);
    // },
    clearAllTodos() {
      this.clearAll()
    },
  },
};
</script>

<style>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}
</style>