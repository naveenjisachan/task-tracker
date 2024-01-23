<!-- src/components/TaskItem.vue -->

<template>
  <div>
    <span>{{ task.name }}</span>
    <button @click="editTask">Edit</button>
    <button @click="deleteTask">Delete</button>
  </div>
</template>

<script>
export default {
  props: {
    task: Object,
  },
  methods: {
    editTask() {
      // Emit event to parent component
      this.$emit("editTask", this.task);
    },
    deleteTask() {
      // Emit event to parent component
      this.$emit("deleteTask", this.task);
    },
  },
};
</script>
