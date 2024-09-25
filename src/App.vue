<script setup>
import { ref } from 'vue';
const header = ref('App lista de compras');
const items = ref([
  {id: '0', label: '10 bolillos'},
  {id: '1', label: '1 lata frijoles'},
  {id: '2', label: '1 Chela'},
  {id: '3', label: '1 Nutela'}
]);

const newitem = ref('');
</script>

<template>
  <h1>
    <i class="material-icons shopping-cart-icon"> local_mall </i>
      {{ header }}
  </h1>
  <input v-model="newItem" type="text" 
  placeholder="Agregar Articulo"> {{ newItem }}

  <ul>
    <li 
      v-for="({ label, id }, i) in items" :key="id"> 
        {{ i+1 }} {{ i%2==0?'🔥':'🛍️' }} {{ label }}</li>
  </ul>
  </template>

<style scoped>
.shopping-cart-icon{
  font-size: 2rem;
}
</style>
