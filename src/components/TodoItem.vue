<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete" />
            {{todo.title}}
            <button @click="$emit('del-todo', todo.id)" class="del">x</button>
        </p>
    </div>
</template>

<script>
    export default {
        name: "TodoItem",
        props: ["todo"],
        methods: {
            markComplete() {
                this.todo.completed = !this.todo.completed
            }
        }
    }
</script>

<style scoped>
    .todo-item {
        background: #f4f4f4;
        padding: 5px;
        border-bottom: 1px #cccccc dotted;
    }

    .is-complete {
        text-decoration: line-through;
    }

    .del {
        background: red;
        background: #42b983;
        color: white;
        border: none;
        padding: 1px 8px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>