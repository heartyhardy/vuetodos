<template>
  <div id="app">
    <div class="title-container"><h1 class="title">Todos</h1></div>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    <div>
      <AddTodo v-on:add-new-todo="addNewTodo" />
    </div>
  </div>
</template>

<script>
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";

export default {
  name: "App",
  components: { Todos, AddTodo },
  data() {
    return {
      todos: [
        {
          id: 0,
          title: "⏰ Wake up",
          completed: true
        },
        {
          id: 1,
          title: "🧘 Meditate",
          completed: false
        },
        {
          id: 2,
          title: "💪 Work out",
          completed: false
        },
        {
          id: 3,
          title: "🥪 Eat",
          completed: false
        },
        {
          id: 4,
          title: "👨‍💻 Code",
          completed: false
        },
        {
          id: 5,
          title: "🛌 Sleep",
          completed: false
        },
        {
          id: 6,
          title: "🔃 Repeat",
          completed: false
        }
      ]
    };
  },
  methods:{
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addNewTodo(newTodo){
      this.todos = [...this.todos, newTodo];
      console.log(this.todos);
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  border: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.5;
  background-color: whitesmoke;
}
.title-container{
  min-width: 100vw;
  position: fixed;
  top:0;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 5px 5rem lightseagreen;
  background-color: #20b2abad;
  border-bottom: 3px solid lightseagreen;
}
.title{
  text-align: center;
  color: darkslategray;
  margin-top: 1rem;
  margin-bottom: 1rem;
}
</style>
