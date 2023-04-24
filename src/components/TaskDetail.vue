<template>
  <div class="task">
    <h3>{{ task.title }}</h3>
    <div class="icons">
      <i @click="taskStore.deleteTask(task.id)" class="ri-delete-bin-fill"></i>
      <i
        @click="taskStore.toggleFav(task.id)"
        class="ri-heart-fill"
        :class="{ active: task.isFav }"
      ></i>
    </div>
  </div>
</template>

<script setup>
import { useTaskStore } from "../stores/TaskStore";

const props = defineProps(["task"]);
const taskStore = useTaskStore();
</script>
