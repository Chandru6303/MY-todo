<!-- src/components/TodoList.vue -->
<template>
    <div class="todo-container">
      <h1>My To-Do List</h1>
      <div class="input-area">
        <input
          v-model="newTodo"
          @keyup.enter="addTodo"
          placeholder="Add a new task"
        />
        <button @click="addTodo">Add</button>
      </div>
      <ul>
        <li v-for="(todo, index) in todos" :key="index" class="todo-item">
          <input type="checkbox" v-model="todo.completed" />
          <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
          <button @click="deleteTodo(index)">Delete</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTodo: "",
        todos: [
          { text: "Buy groceries", completed: false },
          { text: "Read a book", completed: true },
        ],
      };
    },
    methods: {
      addTodo() {
        if (this.newTodo.trim()) {
          this.todos.push({ text: this.newTodo, completed: false });
          this.newTodo = "";
        }
      },
      deleteTodo(index) {
        this.todos.splice(index, 1);
      },
    },
  };
  </script>
  
  <style scoped>
  .todo-container {
    max-width: 400px;
    margin: auto;
  }
  .input-area {
    display: flex;
    margin-bottom: 10px;
  }
  input {
    flex: 1;
    padding: 10px;
  }
  button {
    padding: 10px;
    margin-left: 5px;
  }
  ul {
    list-style: none;
    padding: 0;
  }
  .todo-item {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
  }
  .todo-item input[type="checkbox"] {
    margin-right: 10px;
  }
  .completed {
    text-decoration: line-through;
  }
  </style>
  