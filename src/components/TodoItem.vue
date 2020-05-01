<template>
    <div
     class="todo-item" v-bind:class="{'todo-item-complete': todo.completed }"
     v-on:click="onClick">
        <p>{{todo.title}}</p>
        <p @click="$emit('del-todo',todo.id)">❌</p>
    </div>
</template>

<script>
export default {
    name:"TodoItem",
    props: ['todo'],
    methods:{
        onClick(){
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
    p{
        font-size: large;
    }
    div{
        border-radius: 1rem;
        margin-bottom: 0.5rem;
    }
    .todo-item{
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        background-color: antiquewhite;
        padding: 1rem;
        border-bottom: 3px solid lightcoral;
    }
    .todo-item-complete{
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        color: lightyellow;
        background-color: lightseagreen;
        border-bottom: 3px solid darkgreen;
    }
    .todo-item-complete::before{
        padding-right: 1rem;
        content: '✔️';
        text-shadow: 2px 2px darkgreen;
    }
</style>