<template>
    <!-- <h1>Hello from Todo</h1> -->
    <div class="container">
        <div class="row">
            <div class="col-12">
                <p class="display-3">
                    Vue Crash course
                </p>
            </div>
        </div>
        <div class="row">
             <NewTodo @on-addtodo="addTodo($event)"/>
        </div>
        <div class="row">
            <div class="col-12 col-lg-6">
                <ul class="list-group">
                    <TodoDisplay v-for="(todo, index) in todos" :key="index"
                    :todoString = todo.todostring
                    :completed = todo.completed
                    @on-delete="deleteTodo(todo)"
                    @on-toggle="toggleTodo(todo)"
                    @on-edit="editTodo(todo,$event)"
                    />
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
import TodoDisplay from './TodoDisplay.vue';
import NewTodo from './NewTodo.vue'

export default {
    components : {
        TodoDisplay,
        NewTodo
    },
    data() {
        return {
            todos: [
                { todostring: 'Hey this is me', completed: false },
                { todostring: 'Hey this is you', completed: false },
                { todostring: 'First Vue Project', completed: true },
                { todostring: 'ohh snap!!!', completed: false },
                { todostring: 'Not again!!!', completed: true },
                { todostring: "Let's Create More project", completed: false },
            ]
        }
    },
    methods: {
        addTodo(newTodo) {
            this.todos.push({
                todostring: newTodo,
                completed: false
            });
        },
        toggleTodo(todo) {
            todo.completed = !todo.completed;
        },
        editTodo(todo, newTodoString) {
            todo.todostring = newTodoString;
        },
        deleteTodo(deleteTodo) {
            this.todos = this.todos.filter((todo) => todo.todostring !== deleteTodo.todostring)
        }
    }
}
</script>

<style></style>