src/components/EditTaskForm.vue

<template>
  <div>
    <h2>Edit Task</h2>
    <form @submit.prevent="saveTask">
      <label for="editedTaskName">Task Name:</label>
      <input v-model="editedTaskName" type="text" id="editedTaskName" />
      <label for="editTaskDescription">Task Description:</label>
      <input
        v-model="editTaskDescription"
        type="text"
        id="editTaskDescription"
      />
      <button type="submit">Save Changes</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      editedTaskName: "",
      editTaskDescription: "",
    };
  },
  methods: {
    saveTask() {
      // Handle saving edited task
      console.log(
        "Save edited task:",
        this.editedTaskName,
        this.editTaskDescription
      );
      // Emit event to parent component
      this.$emit("saveTask", [this.editedTaskName, this.editTaskDescription]);
      // Clear input
      this.editedTaskName = "";
      this.editTaskDescription = "";
    },
  },
};
</script>
