<template>
  <div>
    <h2>Task List</h2>
    <ul>
      <li v-for="task in tasks" :key="task.id">
        <TaskItem :task="task" @editTask="editTask" @deleteTask="deleteTask" />
      </li>
    </ul>

    <EditTaskForm
      v-if="editingTask"
      :key="editingTask.id"
      @saveTask="saveTask"
    />
  </div>
</template>

<script>
import TaskItem from "./TaskItem.vue";
import EditTaskForm from "./EditTaskForm.vue";

export default {
  components: {
    TaskItem,
    EditTaskForm,
  },
  props: {
    tasks: Array,
  },
  data() {
    return {
      editingTask: null,
    };
  },
  methods: {
    editTask(task) {
      // Set the editingTask when the "Edit" button is clicked
      this.editingTask = task;
    },
    saveTask(editedTaskName) {
      // Handle saving edited task
      if (this.editingTask) {
        this.editingTask.name = editedTaskName[0];
        this.editingTask.desc = editedTaskName[1];
      }
    },
    deleteTask(task) {
      // Handle deleting task
      this.$emit("deleteTask", task);
      if (this.editingTask === task) {
        this.editingTask = null;
      }
    },
  },
};
</script>
