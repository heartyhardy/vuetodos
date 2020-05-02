<template>
  <div
    v-bind:class="[
      !todo.delted && todo.completed ? 'todo-item-complete':'',
      !todo.deleted && todo.intialized && !todo.completed ? 'todo-item': '',
      !todo.deleted && !todo.intialized ? 'todo-item-init':'',
       todo.deleted ? 'todo-deleted': ''
    ]"
    v-on:click.left.exact="onClick"
    v-on:click.ctrl ="onRightClick(todo.id)"
  >
    <p>{{todo.title}}</p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    onClick() {
      this.todo.completed = !this.todo.completed;
      if (!this.todo.intialized) {
        this.todo.intialized = true;
      }
    },
    onRightClick(id){
      this.todo.deleted = true;
      this.$emit('del-todo', id);
    }
  }
};
</script>

<style scoped>
@keyframes todoOnEnter {
  0% {
    color: lemonchiffon;
    position: relative;
    top: -20px;
    background-color: lightseagreen;
    opacity: 0;
  }
  50%{
      box-shadow: 5px 5px 5rem coral;
  }
  100% {
    position: relative;
    top: 0;
    opacity: 1;
  }
}

@keyframes todoOnComplete {
  0% {
    background-color: antiquewhite;
    box-shadow: 0 0 0 aqua;
  }
  50% {
    background-color: aquamarine;
    box-shadow: 5px 5px 5rem aqua;
  }
  100% {
    background-color: lightseagreen;
  }
}

@keyframes todoOnIncomplete {
  0% {
    background-color: lightseagreen;
    box-shadow: 0 0 0 coral;
  }
  50% {
    background-color: lightsalmon;
    box-shadow: 5px 5px 5rem coral;
  }
  100% {
    background-color: antiquewhite;
  }
}

@keyframes todoOnDelete {
  0% {
    background-color: #FF8B2E;
    box-shadow: 0 0 0 coral;
  }
  50% {
    background-color: lightsalmon;
    box-shadow: 5px 5px 5rem coral;
  }
  100% {
    background-color: antiquewhite;
    opacity: 0;
  }
}


p {
  font-family: 'Jost', sans-serif;
  font-size: larger;
}
div {
  border-radius: 1rem;
  margin-bottom: 0.5rem;
}
.todo-deleted{  
  padding: 1rem;
  animation-name: todoOnDelete;
  animation-duration: 0.5s;
  animation-timing-function: ease-out;
}
.todo-item {
  position: static;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  background-color: antiquewhite;
  padding: 1rem;
  border-bottom: 3px solid lightcoral;
  animation-name: todoOnIncomplete;
  animation-duration: 0.5s;
  animation-timing-function: ease-out;
}
.todo-item-init {
  position: static;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  background-color: antiquewhite;
  padding: 1rem;
  border-bottom: 3px solid lightcoral;
  animation-name: todoOnEnter;
  animation-duration: 0.5s;
  animation-timing-function: ease-out;
}
.todo-item-complete {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-start;
  color: lightyellow;
  padding: 1rem;
  background-color: lightseagreen;
  border-bottom: 3px solid darkgreen;
  animation-name: todoOnComplete;
  animation-duration: 0.5s;
  animation-timing-function: ease-in;
}
.todo-item-complete::before {
  padding-right: 1rem;
  content: "✔️";
  text-shadow: 2px 2px darkgreen;
}
</style>