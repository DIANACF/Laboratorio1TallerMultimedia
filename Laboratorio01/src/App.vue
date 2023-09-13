<script setup>
import { ref } from 'vue';

import listaCompra from './components/icons/listaCompra.vue';

</script>

<template>
<form>
  <p>Articulo</p>
  <input>
  <p>Cantidad</p>
  <input>
  <p>Valor unitario</p>
  <input>
  <br>
  <br>
  <button @click="agregarComp">Agregar</button>

</form>

<listaCompra />

</template>

<style>

form {
  background-color:rgb(12, 10, 32);
  
}
</style>
