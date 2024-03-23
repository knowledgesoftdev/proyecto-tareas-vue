<template>
  <div class="container">
    <div class="text-center">
      <img alt="Vue logo" width="100" height="100" src="./assets/logo.png" />
    </div>
    <TaskComponent :titulo-central="titulo" />
  </div>
</template>

<script setup>
import { ref } from "vue";
import TaskComponent from "./components/TaskComponent.vue";

const titulo = ref("Menu Principal");
</script>


<style scoped>
</style>
