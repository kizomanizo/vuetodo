<template>
    <div>
        <form class="form-inline" @submit="addTodo">
            <div class="form-group mb-2">
                <p>Add a new Todo</p>
            </div>
            <div class="form-group mx-sm-3 mb-2">
                <input type="text" v-model="title" class="form-control" name="title" id="title" placeholder="Task...">
            </div>
            <input type="submit" value="Submit" class="btn btn-secondary mb-2">
        </form>
    </div>
</template>

<script>
// import { v4 as uuidv4 } from 'uuid';

export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault()
            const newTodo = {
                // id: uuidv4(),
                title: this.title,
                completed: false
            };
            // Send to parent
            this.$emit('add-todo', newTodo);

            // Empty the input field
            this.title = "";
        }
    }
}
</script>

<style scoped>
    
</style>