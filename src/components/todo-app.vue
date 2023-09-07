<template>
  <div>
    <h1 class="app-title">Welcome to My Todo App</h1>
  </div>
  <div id="app">
    <h1>Todo App</h1>

    <!-- Input for adding new todo items -->
    <div class="input-container">
      <input v-model="newTodo" @keyup.enter="addTodo" type="text" placeholder="Insert a new sentence." class="center-input" :style="{ 'font-weight': isBold ? 'bold' : 'normal' }">
    </div>

    <!-- List of todo items -->
    <ul class="todo-list">
      <li v-for="(todo, index) in todos" :key="index" class="todo-item">
        <div class="todo-item-inner">
          <input type="checkbox" v-model="todo.completed" class="todo-checkbox">
          <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
        </div>
        <button @click="removeTodo(index)" class="delete-button">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: [],
      isBold: false, // Add a data property to control font weight
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push({ text: this.newTodo, completed: false });
        this.newTodo = '';
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  },
  watch: {
    newTodo: function (newValue) {
      // Check if the input is not empty, and set isBold to true if it's not
      this.isBold = newValue.trim() !== '';
    }
  }
};
</script>

<style>
:root {
  --primary-color: purple; /* Purple */
  --secondary-color: #d400aa; /* Pink */
}

.app-title {
  font-size: 20px;
  color: white;
  text-align: center;
  margin-top: 20px;
  margin-bottom: 20px;
}

.center-input {
  width: 80%;
  margin: 0 auto;
  display: block;
  padding: 10px;
  border: 1px solid #692051;
  border-radius: 5px;
  font-size: 16px;
}

body {
  background-color:black; 
  margin: 0;
  padding: 0;
}

#app {
  font-family: 'Arial', sans-serif;
  font-size: 20px;
  text-align: center;
  margin: 20px auto; 
  max-width: 400px; 
  background-image: linear-gradient(to bottom, var(--primary-color), var(--secondary-color));
  color:grey; 
  padding: 15px;
  border-radius: 10px;
  box-shadow: 0px 6px 10px rgba(0, 0, 0, 0.4);
}
.input-container {
  margin-bottom: 18px;
}

.todo-list {
  list-style: none;
  padding: 0;
}

.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 15px;
  background-color: rgba(255, 255, 255, 0.1);
  border-radius: 10px;
  padding: 15px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
  transition: background-color 0.2s ease-in-out;
}

.todo-item:hover {
  background-color: rgba(0, 0, 0, 0.3);
}

.todo-checkbox {
  margin-right: 20px;
  transform: scale(1.2);
}

.completed {
  text-decoration: line-through;
}

.delete-button {
  background-color: #36b1f4; /* blue */
  color: white;
  border: none;
  padding: 5px 12px;
  margin-left: 10px;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.2s ease-in-out;
}

.delete-button:hover {
  background-color: #d32f86; /* Darker pink */
}

.todo-item-inner {
  display: flex;
  align-items: center;
}
</style>

