<template>
    <div class="container">
        <div v-bind:key="todo.key" v-for="todo in todos">
            <TodoItem v-bind:todo="todo"/>
        </div>
    </div>
</template>

<script>

import TodoItem from './TodoItem';

export default {
    name: 'Todos',
    components: {
        TodoItem
    },
    props: ['todos']
}
</script>

<style scoped>
    .container{
        padding: 2rem;
    }
</style>