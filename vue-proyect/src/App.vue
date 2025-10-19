<script setup>
import { ref } from 'vue';
import Formulario from './components/Formulario.vue';
import Tabla from './components/Tabla.Reactiva.vue';

// Array para almacenar todos los estudiantes
const estudiantes = ref([]);


// Función para agregar un estudiante a la lista
const agregarEstudiante = (estudiante) => {
  
  estudiantes.value.push({
    ...estudiante
  });
};
</script>

<template>
<Formulario @agregar-estudiante="agregarEstudiante"> </Formulario>
<Tabla :estudiantes="estudiantes"> </Tabla>


</template>

<style >


</style>

