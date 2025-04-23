<script setup>

import { ref } from 'vue';

const name = ref('John Doe');
const status = ref('active');
const tasks = ref(['Task one', 'Task two', 'Task three']);
const toggleStatus = () => {
  if (status.value === 'active') {
    status.value = 'pending';
  } else if (status.value === 'pending') {
    status.value = 'inactive';
  } else if (status.value === 'inactive') {
    status.value = 'active';
  }
}

</script>

<template>
  <h1>Vue Jobs</h1>
  <p v-if="status === 'active'">{{ name }}</p>
  <p v-else-if="status === 'pending'">pending</p>
  <p v-else="status === 'inactive'">User is inactive</p>
  <h3>Tasks</h3>
  <ul>
    <li v-for="task of tasks" :key="task">{{ task }}</li>
  </ul>
  <button v-on:click="toggleStatus">status</button>

</template>

<style></style>