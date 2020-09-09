<template>
    <div id="home">
        <main v-if="loading">
            <Spinner />
        </main>
        <!-- Natupia content hapa -->
        <main v-else role="main" class="container">
            <AddTodo v-on:add-todo="addTodo" />
            <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
        </main>
    </div>
</template>

<script>
    import AddTodo from '../components/AddTodo';
    import Todos from '../components/Todos';
    import axios from "axios";
    import Spinner from "../components/layout/Spinner";

    export default {
        name: 'App',
        components: {
            AddTodo,
            Todos, 
            Spinner,
        },
        data() {
            return {
                todos: [],
                loading: false
            }
        },
        methods: {
            deleteTodo(id) {
                axios.delete(`https://jsonplaceholder.typicode.com/todos${id}`)
                .then(this.todos = this.todos.filter(todo => todo.id !== id))
                .catch(err => console.log(err));
                // this.todos = this.todos.filter(todo => todo.id !== id);
            },
            addTodo(newTodo) {
                const { title, completed } = newTodo;
                axios.post("https://jsonplaceholder.typicode.com/todos", {
                    title, // ES6 for title: title
                    completed,
                })
                .then(res => this.todos = [...this.todos, res.data])
                .catch(err => console.log(err));
                // this.todos = [...this.todos, newTodo];
            }
        },
        created() {
            this.loading = true
            axios.get("https://jsonplaceholder.typicode.com/todos?_limit=10")
            .then(res => this.todos = res.data)
            .catch(err => console.log(err))
            .finally(() => (this.loading = false));
        }
    }
</script>

<style>
    #home {
      text-align: left !important;
    }
</style>