<template>
  <main>

    <!-- heading -->
    <header>
      <img src="https://pinia.vuejs.org/logo.svg" alt="pinia logo">
      <h1>Pinia Tasks</h1>
    </header>

    <div class="new-task-form">
      <TaskForm />
    </div>

    <nav class="filter">
      <button @click="filter = 'all'">All tasks</button>
      <button @click="filter = 'favs'">Fav tasks</button>
    </nav>

    <div class="loading" v-if="taskStore.loading">
      Loading tasks...
    </div>

    <div class="task-list" v-if="filter === 'all'">
      <p>You have {{ taskStore.totalCount }} tasks left to do</p>
      <div v-for="task in taskStore.tasks">
        <TaskDetails :task="task"/>
      </div>
    </div>

    <div class="task-list" v-if="filter === 'favs'">
      <p><p>You have {{ taskStore.favCount }} favs left to do</p></p>
      <div v-for="task in taskStore.favs">
        <TaskDetails :task="task"/>
      </div>
    </div>

  </main>
</template>

<script setup>
import { useTaskStore } from './stores/TaskStore';
import TaskDetails from './components/TaskDetails.vue';
import TaskForm from './components/TaskForm.vue';
import { ref } from 'vue'

const taskStore = useTaskStore()

taskStore.getTasks()

const filter = ref('all')
</script>
