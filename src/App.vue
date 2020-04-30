<template>
  <div id="app">
    <h1 class="title">Todos</h1>
    <Todos v-bind:todos="todos" />
  </div>
</template>

<script>
import Todos from "./components/Todos";

export default {
  name: "App",
  components: { Todos },
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
.title{
  text-align: center;
  color: darkslategray;
  margin-top: 1rem;
}
</style>
