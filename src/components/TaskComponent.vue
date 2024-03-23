<template>
  <div>
    <h1 class="text-center">{{ tituloCentral }}</h1>
    <div class="row">
      <div class="col-6">
        <FormTaskComponent @enviar-formulario="addTarea" />
      </div>
      <div class="col-6">
        <h3 class="text-center">Listar Tareas</h3>
        <table class="table table-bordered table-success">
          <thead class="text-center">
            <th>TITULO</th>
            <th>ESTADO</th>
            <th>OPCIÓN</th>
          </thead>
          <tbody class="text-center">
            <tr v-if="tasks.length === 0">
              <td colspan="3">No hay tareas</td>
            </tr>
            <tr v-for="(task, index) in tasks" :key="index" :class="{ 'table-success': task.estado, 'table-danger': !task.estado }">
              <td>{{ task.titulo.toUpperCase() }}</td>
              <td>{{ task.estado ? "COMPLETADO" : "PENDIENTE" }}</td>
              <td>
                <button class="btn btn-danger btn-sm" @click="eliminar(index)">E</button> |
                <button @click="cambiarEstado(index)" class="btn btn-info btn-sm">
                  C
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps, ref } from "vue";
import FormTaskComponent from "./FormTaskComponent.vue";

defineProps({
  tituloCentral: {
    type: String,
    required: true,
  },
});

const tasks = ref([]);

const addTarea = (valor) => {
  tasks.value.push(valor);
};

const cambiarEstado = (index) => {
  tasks.value[index].estado = !tasks.value[index].estado;
};

const eliminar=(index)=>{
    tasks.value.splice(index, 1);   
}
</script>

<style scoped>
</style>
