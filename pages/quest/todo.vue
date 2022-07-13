<script>
let id = 0
export default {
    data() {
        return {
            newTodo: '',
            todos: [],
            activecheck: 0
        }
    },
    methods: {
        addTodo() {
            this.todos.push({ id: id, text: this.newTodo, done: false })
            this.newTodo = ''
            id++
        },
        removeTodo(todo) {
            this.todos = this.todos.filter((t) => t !== todo)
        },
        checkchange(num) {
            this.activecheck = num
        }
    }
}
</script>

<template>
    <h1>Todo List</h1>
    <div class="add">
        <form @submit.prevent="addTodo">
            <input v-model="newTodo" placeholder="무엇을 하나요?">
        </form>
    </div>
    <div class="list" v-if="todos.length != 0">
        <ul v-if="activecheck === 0">
            <li v-for="todo in todos" :key="todo.id">
                <input type="checkbox" v-model="todo.done">
                <span :class="{ done: todo.done }"> {{ todo.text }} </span>
                <button @click="removeTodo(todo)">X</button>
            </li>
        </ul>
        <ul v-if="activecheck === 1">
            <li v-for="todo in todos" :key="todo.id">
                <div v-if="todo.done === false">
                    <input type="checkbox" v-model="todo.done">
                    <span :class="{ done: todo.done }"> {{ todo.text }} </span>
                    <button @click="removeTodo(todo)">X</button>
                </div>
            </li>
        </ul>
        <ul v-if="activecheck === 2">
            <li v-for="todo in todos" :key="todo.id" v-if="todos.done === true">
                    <input type="checkbox" v-model="todo.done">
                    <span :class="{ done: todo.done }"> {{ todo.text }} </span>
                    <button @click="removeTodo(todo)">X</button>
            </li>
        </ul>
        <p> {{ this.todos.filter(v => v.done === false).length }} items left</p>
    </div>
    <div>
        <button @click="checkchange(0)">All</button><br />
        <button @click="checkchange(1)">Active</button><br />
        <button @click="checkchange(2)">Completed</button>
    </div>
</template>

<style>
.done {
    text-decoration: line-through;
}

button {
    background-color: black;
    color: white;
}
</style>