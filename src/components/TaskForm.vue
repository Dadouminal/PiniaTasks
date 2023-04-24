<template>
  <form @submit.prevent="handleSubmit">
    <input type="text" placeholder="I need to..." v-model="newTask" />
    <button>add</button>
  </form>
</template>

<script setup>
import { ref } from "vue";
import { useTaskStore } from "../stores/TaskStore";

const newTask = ref("");
const taskStore = useTaskStore();

const handleSubmit = () => {
  if (newTask.value.length > 0) {
    taskStore.addTask({
      id: Math.floor(Math.random() * 10000),
      title: newTask.value,
      isFav: false,
    });
    newTask.value = "";
  }
};
</script>
