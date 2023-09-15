<script setup>
import { ref, computed } from 'vue';

const NomArticulo = ref(''); 
const Cantidad = ref(0);      
const valorunit = ref(0);     
const compras = ref([]);  
const newCompra = ref('');    

const agregarCompra = () => {
  
  if (NomArticulo.value && Cantidad.value > 0 && valorunit.value > 0) {
    const valorTotal = Cantidad.value * valorunit.value;
   
    compras.value.push({
      NomArticulo: NomArticulo.value,
      Cantidad: Cantidad.value,
      valorunit: valorunit.value,
      valorTotal,
    });
    NomArticulo.value = '';
    Cantidad.value = 0;
    valorunit.value = 0;
  }
}; 




const eliminarCompra = (index) => {
  compras.value.splice(index, 1);
};

const totalCompra = computed(() => {
  return compras.value.reduce((total, compra) => total + compra.valorTotal, 0);
});


const descuento = computed(() => {
  let descuentoCantidad = 0;
  let descuentoPrecio = 0;

  if (totalCompra.value >= 120000) {
    descuentoPrecio = totalCompra.value * 0.1;
  } else if (totalCompra.value >= 60000) {
    descuentoPrecio = totalCompra.value * 0.05;
  }

  if (compras.value.length >= 12) {
    descuentoCantidad = totalCompra.value * 0.2;
  } else if (compras.value.length >= 6) {
    descuentoCantidad = totalCompra.value * 0.1;
  }

  // Selecciona el mayor descuento entre descuentoCantidad y descuentoPrecio
  return Math.max(descuentoCantidad, descuentoPrecio);
});


const totalAPagar = computed(() => {
  return totalCompra.value - descuento.value;
});

</script>

<template>
  <!--formulario para agregar productos-->
<form @submit.prevent="agregarCompra" class="ubicar">
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
  <button @click="agregarCompra">Agregar</button>

</form>
<br>
    <table class="ubicar">
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
            <tr v-for="(producto, index) in compras" :key="index">
            <td>{{ index + 1 }}</td>
            <td>{{ producto.NomArticulo }}</td>
            <td>{{ producto.Cantidad }}</td>
            <td>{{ producto.valorunit }}</td>
            <td>{{ producto.valorTotal }}</td>
            <td><button @click="eliminarCompra">Eliminar</button></td>

        </tr>
        </tbody>
    </table>
    <br>
    <p>Total Compra: {{ totalCompra }}</p>
    <p>Descuento: {{ descuento }}</p>
    <p>Total a pagar: {{ totalAPagar }} </p>
</template>

<style>

form {
  background-color:rgb(12, 10, 32);
  
  
}

table, th, td {
  border: 1px solid;
}

/*.ubicar {
  display: grid;
  grid-template-columns: 1fr 1fr;

}*/


</style>
