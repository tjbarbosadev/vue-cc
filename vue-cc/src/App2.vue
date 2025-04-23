<script setup>

import { ref } from 'vue';

const name = ref('John Doe');
const status = ref('active');
const tasks = ref(['Task one', 'Task two', 'Task three']);
const newTask = ref('');

const toggleStatus = () => {
  if (status.value === 'active') {
    status.value = 'pending';
  } else if (status.value === 'pending') {
    status.value = 'inactive';
  } else if (status.value === 'inactive') {
    status.value = 'active';
  }
}

const addTask = () => {
  if (newTask.value.trim() !== '') {
    tasks.value.push(newTask.value);
    newTask.value = '';
  }
}

const deleteTask = item => {
  tasks.value.splice(item, 1);
}

</script>

<template>
  <h1>Vue Jobs</h1>
  <p v-if="status === 'active'">{{ name }}</p>
  <p v-else-if="status === 'pending'">pending</p>
  <p v-else="status === 'inactive'">User is inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">create</button>
  </form>

  <h3>Tasks</h3>
  <ul>
    <li v-for="(task, index) of tasks" :key="task">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">x</button>
    </li>
  </ul>
  <button v-on:click="toggleStatus">status</button>

</template>

<style></style>