<!-- src/App.vue -->

<template>
  <div id="app">
    <AddTaskForm @addTask="addTask" />
    <TaskList :tasks="tasks" @editTask="editTask" @deleteTask="deleteTask" />
    <EditTaskForm v-if="editingTask" @saveTask="saveTask" />
  </div>
</template>

<script>
import AddTaskForm from "./components/AddTaskForm.vue";
import TaskList from "./components/TaskList.vue";
import EditTaskForm from "./components/EditTaskForm.vue";

export default {
  components: {
    AddTaskForm,
    TaskList,
    EditTaskForm,
  },
  data() {
    return {
      tasks: [
        { id: 1, name: "Task 1", desc: "Task 1 Desc" },
        { id: 2, name: "Task 2", desc: "Task 2 Desc" },
        // ... initial tasks
      ],
      editingTask: null,
    };
  },
  methods: {
    addTask(newTaskName) {
      // Handle adding task
      const newTask = {
        id: Date.now(),
        name: newTaskName[0],
        desc: newTaskName[1],
      };
      this.tasks.push(newTask);
    },
    editTask(task) {
      // Handle initiating task edit
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
      this.tasks = this.tasks.filter((t) => t !== task);
      if (this.editingTask === task) {
        this.editingTask = null;
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
