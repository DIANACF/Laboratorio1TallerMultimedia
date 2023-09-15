<script setup>
import { ref } from 'vue';



 //newCompra: [];
//const Compra = ref([{
  //NomArticulo: '',
  //Cantidad: 0,
  //valorunit: 0,
//}]);

</script>

<template>
  <!--formulario para agregar productos-->
<form @submit.prevent="agregarCompra">
  <label for="NomArticulo">Articulo: </label>
  <br>
  <input v-model="NomArticulo" type="text" id="NomArticulo">
  <br>
  <label for="Cantidad">Cantidad: </label>
  <br>
  <input v-model.number="Cantidad" type="number" id="Cantidad">
  <br>
  <label for="valorunit">Valor Unitario: </label>
  <br>
  <input v-model.number="valorunit" type="number" id="valorunit">
  <br>
  <br>
  <button @click="agregarComp">Agregar</button>

</form>
<br>
    <table id="TablaCompras">
        <thead>
            <tr>
            <th>#</th>
            <th>Articulo</th>
            <th>Cantidad</th>
            <th>V.unitario</th>
            <th>Total</th>
            <th></th>
        </tr>
        </thead>
        <tbody>
            <tr>
            <td> </td>
            <td>A1</td>
            <td>2</td>
            <td>1000</td>
            <td>2000</td>
            <td><button>Eliminar</button></td>

        </tr>
        </tbody>
    </table>
    <br>
    <p>Total Compra: </p>
    <input>
    <p>Descuento: </p>
    <input>
    <p>Total a pagar: </p>
    <input>
</template>

<style>

form {
  background-color:rgb(12, 10, 32);
  
}
</style>
