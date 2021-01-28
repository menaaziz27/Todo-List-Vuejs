<template>
  <div id="app">
    <Header />
    <AddTodo @add-todo="addTodo" />
    <Todos v-bind:todos="todos" @del-todo="delTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import AddTodo from "./components/AddTodo.vue";
import Header from "./components/layout/Header";

export default {
  name: "App",
  components: {
    Todos,
    AddTodo,
    Header,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push(newTodo);
      console.log(this.todos);
    },

    delTodo(todoTitle) {
      this.todos = this.todos.filter((todo) => !todo.title.includes(todoTitle));
      console.info(this.todos, "delTodo");
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
