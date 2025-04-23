<script>
export default {
  data() {
    return {
      name: 'John Doe',
      status: 'inactive',
      tasks: ['Task one', 'Task two', 'Task three'],
      link: 'https://google.com'
    }
  },
  methods: {
    toggleStatus() {
      if (this.status === 'active') {
        this.status = 'pending';
      } else if (this.status === 'pending') {
        this.status = 'inactive';
      } else if (this.status === 'inactive') {
        this.status = 'active';
      }
    }
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
  <a v-bind:href="link">google.com</a>
  <button v-on:click="toggleStatus">status</button>

</template>

<style></style>