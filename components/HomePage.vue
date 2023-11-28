<template>
  <div>
    <div class="wrapper">
      <h2>PHP To Do List</h2>
      <p>Task is added successfully</p>

      <form @submit.prevent="addTodo" class="inputField">
        <input v-model="newTodo" placeholder="Enter Something..." />
        <button type="submit">Add</button>
      </form>

      <ul class="todoList">
        <li v-for="(todo, index) in todos" :key="index">
          {{ todo.text }}
          <span><button @click="deleteTodo(index)"><i class="ri-delete-bin-5-fill"></i></button></span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>

import { ref, reactive } from "vue";

const todos = ref([]);

const newTodo = ref("");

//methods
const addTodo = () => {
  if (newTodo.value.trim() != "") {
    todos.value.push({ text: newTodo.value, completed: false });
    newTodo.value = "";
  }};

const deleteTodo = (index) => {
  todos.value.splice(index, 1);
};
</script>
