<template>
  <main>
    <header>
      <img src="./assets/logo-pinia.svg" alt="pinia logo" />
      <h1>Pinia Tasks</h1>
    </header>
    <div class="new-task-form">
      <TaskForm />
    </div>
    <nav class="filter">
      <button @click="filter = 'all'">All tasks</button>
      <button @click="filter = 'favs'">Fav tasks</button>
    </nav>
    <div class="task-list" v-if="filter === 'all'">
      <p>You have {{ taskStore.totalCount }} tasks left to do</p>
      <div v-for="task in taskStore.tasks">
        <TaskDetail :task="task" />
      </div>
    </div>
    <div class="task-list" v-if="filter === 'favs'">
      <p>You have {{ taskStore.favCount }} favs left to do</p>
      <div v-for="task in taskStore.favs">
        <TaskDetail :task="task" />
      </div>
    </div>
  </main>
</template>

<script setup>
import { useTaskStore } from "./stores/TaskStore";
import TaskDetail from "./components/TaskDetail.vue";
import { ref } from "vue";
import TaskForm from "./components/TaskForm.vue";

const filter = ref("all");

const taskStore = useTaskStore();
</script>
