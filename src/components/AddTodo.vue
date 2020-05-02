<template>
  <div class="add-todo-floating">
    <input class="text-input" type="text" v-model="title" name="title" autocomplete="off" placeholder="Add a title" />
    <button class="add-todo-btn" v-on:click="addTodo">➕</button>
  </div>
</template>

<script>
import { v4 as uuidv4 } from "uuid";

export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo() {
      const newTodoItem = {
        id: uuidv4(),
        title: "📌 " + this.title,
        completed: false,
        initialized: false,
        deleted: false
      };
      this.$emit("add-new-todo", newTodoItem);
    }
  }
};
</script>

<style scoped>

@keyframes onBtnClick {
  0% {
    background-color: #325FBE;
  }
  50%{
    background-color: lightsalmon;
  }
  100%{
    background-color: #FF8B2E;
  }
}

.text-input {
  outline-style: none;
  padding: 0.5rem;
  background-color: lightblue;
  border: 2px solid skyblue;
  border-radius: 5px;
  min-width: 75vw;
}
.text-input:focus{
  border: 3px solid aqua;
}
.add-todo-btn {
  color: wheat;
  background-color: #325FBE;
  padding: 0.5rem;
  margin-left: 0.5rem;
  font-size: large;
  min-width: 10vw;
  border-radius: 5px;
  outline-style: none;
}
.add-todo-btn:focus{
  animation-name: onBtnClick;
  animation-duration: 0.5s;
  animation-timing-function: ease-out;
  background-color:#FF8B2E;
}
.add-todo-floating {
  position: fixed;
  bottom: 0;
  background-color: #20b2abad;
  border-top: 3px solid lightseagreen;
  box-shadow: 0 -5px 5rem lightseagreen;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem;
  min-width: 100vw;
}
</style>