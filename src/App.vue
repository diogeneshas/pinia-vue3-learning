<template>
  <main>

    <!-- heading -->
    <header>
      <img src="https://pinia.vuejs.org/logo.svg" alt="pinia logo">
      <h1>Pinia Tasks</h1>
    </header>

    <div class="task-list">
      <div v-for="task in taskStore.tasks">
        <TaskDetails :task="task"/>
      </div>
    </div>

  </main>
</template>

<script setup>
import { useTaskStore } from './stores/TaskStore';
import TaskDetails from './components/TaskDetails.vue';

const taskStore = useTaskStore()
</script>
