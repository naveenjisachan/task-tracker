<!-- src/components/AddTaskForm.vue -->

<template>
  <div>
    <h2>Add Task</h2>
    <form @submit.prevent="addTask">
      <label for="newTaskName">Task Name:</label>
      <input v-model="newTaskName" type="text" id="newTaskName" />
      <label for="newTaskDescription">Task Description:</label>
      <input v-model="newTaskDescription" type="text" id="newTaskDescription" />
      <button type="submit">Add Task</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTaskName: "",
      newTaskDescription: "",
    };
  },
  methods: {
    addTask() {
      // Handle adding task
      console.log("Add task:", this.newTaskName, this.newTaskDescription);
      // Emit event to parent component
      this.$emit("addTask", [this.newTaskName, this.newTaskDescription]);
      // Clear input
      this.newTaskName = "";
      this.newTaskDescription = "";
    },
  },
};
</script>
