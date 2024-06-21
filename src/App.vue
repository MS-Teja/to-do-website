<script>
export default {
  name: 'App',
  data() {
    return {
      newTask: '',
      tasks: []
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== '') {
        this.tasks.push({ text: this.newTask, completed: false });
        this.newTask = '';
      }
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    toggleCompletion(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
    }
  }
};
</script>

<template>
  <div id="app">
    <input v-model="newTask" @keyup.enter="addTask" placeholder="Add a new task" />
    <button @click="addTask">Add Task</button>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <span :class="{ completed: task.completed }" @click="toggleCompletion(index)">{{ task.text }}</span>
        <button @click="deleteTask(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.completed {
  text-decoration: line-through;
}
</style>