<script setup>
import { reactive } from 'vue';

// Definir el evento que se emitirá al componente padre
const emit = defineEmits(['agregar-estudiante']);

const estudiante=reactive({
    nombre:"",
    apellido:"",
    ci:"",
    nuevoIngreso:"false"
})


const handleSubmit=()=>{
    let carnet=/^\d{11}$/;
    let caracteres=/^[A-Za-z]+$/;
    let esValido=true
    if(!carnet.test(estudiante.ci)){
        alert("Carnet incorrecto, verificar 11 digitos ")
        esValido=false;
    }else if(!caracteres.test(estudiante.nombre)){
    alert("Error: Nombre solo acepta carácteres")
    esValido=false;
    }else if(!caracteres.test(estudiante.apellido)){
        alert("Error: Apellido solo acepta carácteres");
        esValido = false;
    }
    
    // Si todas las validaciones pasan, emitir el evento
    if(esValido){
        // Emitir el estudiante al componente padre
        emit('agregar-estudiante', {
            nombre: estudiante.nombre,
            apellido: estudiante.apellido,
            ci: estudiante.ci,
            nuevoIngreso: estudiante.nuevoIngreso
        });
        
        
        // Limpiar el formulario
        estudiante.nombre = '';
        estudiante.apellido = '';
        estudiante.ci = '';
        estudiante.nuevoIngreso = 'false';
    }
}


</script>

<template>
<form @submit.prevent="handleSubmit" class="form">
    <h1>Agregar Estudiante</h1>

<div class=" form-input"> 
    <label >Nombre 
<input type="text" id="nombre" v-model="estudiante.nombre" placeholder="A-Z" required>
    </label> 

    <label > Apellido
        <input type="text" id="apellido" v-model="estudiante.apellido" placeholder="A-Z" required>
    </label>

    <label >CI
    <input type="text"  id="ci" v-model="estudiante.ci" >
    </label>

    <label for="chekbox" >Nuevo Ingreso </label>
<input type="checkbox" class="chekbox" v-model="estudiante.nuevoIngreso" id="chekbox">
</div>

<button type="submit" id="agregar"> Agregar Estudiante</button>

</form>
</template>

<style >

body{
    background-color: #eee;
    font-family: sans-serif;
margin: 0;
color: black;

}

.form{
background-color: transparent;
padding: 10px 0;
width: 500px;
margin: auto;
margin-top: 50px;
display: flex;
flex-direction: column;
gap: 1rem;
border-radius: 10px  ;
}


.form-input{
    padding: 10px 10px;
}

input[type="text"]{
width: 100%;
box-sizing: border-box; 
border: 2px solid #666;
background-color: transparent;
border-radius: 5px;
padding: 8px ;
color:black;
}

.chekbox{
    width: auto;
    height: auto;
    margin-left: 10px;
}

h1{
    text-align: center;
    font-size: 40px;
}

h1:hover{
    color:  rgb(26, 175, 168);
}

label{
    font-size: 16px;
    line-height: 1.5;
}

label:hover{
    color:  rgb(26, 175, 168);
}

button{
    background-color: rgb(0,0,255);
    color: white;
    padding: 7px 7px;
    border-radius: 4px;
    margin: 10px auto;
}

.valido{
    border-color: #4CAF50 ;
    background-color: #e6ffe6 ;
}
.invalido{
    background-color: #ffe6e6  ;
    border-color: #f44336 ;
    
}
</style>

