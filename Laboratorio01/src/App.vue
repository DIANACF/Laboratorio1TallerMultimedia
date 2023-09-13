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
  <button>Agregar</button>

</form>

<listaCompra />

</template>

<style>

</style>
