<script setup>
// Recibir la lista de estudiantes como prop
defineProps({
    estudiantes: {
        type: Array,
        required: true
    }
});
</script>

<template>
    <div >
    
    <h1>Listado de Estudiantes</h1>

<table>
    <thead>
        <tr>
    <th>Nombre</th>
    <th>Apellido</th>
    <th>CI</th>
    <th>Es nuevo ingreso?</th>
</tr>
    </thead>
    <tbody>
        <tr v-if="estudiantes.length === 0">
            <td colspan="4" style="text-align: center; color: #999;">
                No hay estudiantes registrados
            </td>
        </tr>
        <tr v-for="estudiante in estudiantes" :key="estudiante.id">
            <td>{{ estudiante.nombre }}</td>
            <td>{{ estudiante.apellido }}</td>
            <td>{{ estudiante.ci }}</td>
            <td>{{ estudiante.nuevoIngreso === 'true' || estudiante.nuevoIngreso === true ? 'Sí' : 'No' }}</td>
        </tr>
    </tbody>

</table>

</div>
</template>

<style>

body{
    background-color: #eee;
    font-family: sans-serif;
margin: 0;
color: black;
 padding: 40px 20px;
}

div{
    max-width: 1000px;
    margin: 0 auto;
    background-color: white;
    padding: 40px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    }


table {
    width: 100%;
    border-collapse: collapse;
}

td {
    padding: 20px;
    color: #666;
    font-size: 1.05em;
    border-bottom: 1px solid #e0e0e0;
    }
tr:last-child td {
            border-bottom: none;
        }

        tr:hover {
            background-color: #f9f9f9;
        }

        @media (max-width: 768px) {
            .container {
                padding: 20px;
            }
        

            h1 {
                font-size: 1.8em;
            }

            th, td {
                padding: 12px 8px;
                font-size: 0.9em;
            }
        }
th {
            background-color: #e8e8e8;
            color: #555;
            padding: 20px;
            text-align: left;
            font-size: 1.1em;
            font-weight: 600;
        }

h1{
    text-align: center;
    color: #333;
            font-size: 2.5em;
            margin-bottom: 40px;
            font-weight: normal;
}


</style>