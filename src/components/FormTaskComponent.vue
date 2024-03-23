<template>
  <div>
    <h3 class="text-center">Formulario de Tareas</h3>
    <div class="form-group">
      <label for="titulo">Titulo de la tarea</label>
      <input
        id="titulo"
        class="form-control"
        type="text"
        v-model="task.titulo"
      />
      <button class="btn btn-success mt-2" @click="enviarTarea">Guardar</button>
    </div>
  </div>
</template>

<script setup>
import { defineEmits, ref } from "vue";

const task = ref({
  titulo: "",
  estado: false,
});

const enviarTarea = () => {
  emit("enviar-formulario", task.value);
  task.value = {
    titulo:"",
    estado:false
  }
};

const emit = defineEmits(["enviar-formulario"]);
</script>

<style>
</style>
