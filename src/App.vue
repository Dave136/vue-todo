<template>
  <h1>Vue 3 Todo App</h1>
  <form @submit.prevent="addNewTodo">
    <label>New Todo</label>
    <input v-model="newTodo" type="text" name="newTodo">
    <button>Add new Todo</button>
  </form>
  <button @click="removeAllTodos">Remove All</button>
  <button @click="markAllDone">Mark All Done</button>
  <h2>{{ newTodo }}</h2>
  <ul>
    <li v-for="(todo, index) in todos" :key="todo.id" class="todo">
      <h3 :class="{ done: todo.done }" @click="toggleDone(todo)">{{ todo.content }}</h3>
      <button @click="removeTodo(index)">Remove Todo</button>
    </li>
  </ul>
</template>

<script>
// BASIC WAY USING COMPOSITION API
// import { ref } from "vue";

// export default {
  // setup() {
  //   const newTodo = ref("");
  //   const todos = ref([]);

  //   function addNewTodo() {
  //     todos.value.push({
  //       id: Date.now(),
  //       done: false,
  //       content: newTodo.value
  //     });

  //     newTodo.value = "";
  //   }

//     function toggleDone(todo) {
//       todo.done = !todo.done;
//     }

//     function removeTodo(index) {
//       todos.value.splice(index, 1);
//     }

//     function markAllDone() {
//       todos.value.forEach(todo => todo.done = true);
//     }

//     function removeAllTodos() {
//       todos.value = [];
//     }

//     return { todos, newTodo, addNewTodo, removeTodo, toggleDone, markAllDone, removeAllTodos };
//   }
// }
</script>

<script setup>
import { ref } from "vue";

export const newTodo = ref(""); 
export const todos = ref([]);

export function addNewTodo() {
  todos.value.push({
    id: Date.now(),
    done: false,
    content: newTodo.value
  });

  newTodo.value = "";
}

export function toggleDone(todo) {
  todo.done = !todo.done;
}

export function removeTodo(index) {
  todos.value.splice(index, 1);
}

export function markAllDone() {
  todos.value.forEach(todo => todo.done = true);
}

export function removeAllTodos() {
  todos.value = [];
}

</script>

<style>
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.todo {
  cursor: pointer;
}

.done {
  text-decoration: line-through;
}
</style>
