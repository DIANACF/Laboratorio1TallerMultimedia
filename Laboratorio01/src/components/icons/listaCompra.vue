<script setup>
import { ref } from 'vue';

let TablaId = 1;

const newCompra = ref('');
const Compra = ref([{id: TablaId++,
     Articulo: 'A1',
      Cantidad: 0, 
      Vunitario: 0,
      Total: number}]);

function agregarComp () {
    Compra.value.push ()
    newCompra.value = ''
}


</script>

<template>
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
            <td> {{ id }}</td>
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
table {
    border: 1px solid white

}
</style>