<script setup>
import { ref } from 'vue'
// Modelo
const header = ref('App lista de compras')
//items
//item-model
const items = ref([
{id: '0', label: '10 bolillos'},
  {id: '1', label: '1 lata frijoles'},
  {id: '2', label: '1 Chela'},
  {id: '3', label: '1 Nutela'}
]);
//item-Method
const saveItem = () =>
{
   items.value.push({id: items.value.length + 1, label: newItem.value});
   //clean the imput-Limpia el imput
   newItem.value = '';
};
// --- Formulario ---
const newItem = ref('')
const newItemHighPriority = ref(false)
const editing = ref(true);   
const activateEdition = (activate) => {
  editing.value = activate;
}
</script>

<template>
  <div>
    <h1>
      <i 
        class="material-icons shopping-cart-icon">
        local_mall
      </i>
      {{ header }}
    </h1>  
    <button 
      v-if="editing" 
      class="btn" 
      @click="activateEdition(false)">
        Cancelar
      </button>
    <button 
      v-else 
      class="btn btn-primary"
      @click="activateEdition(true)">
        Agregar Articulo
    </button>
       
   </div>

  <form
    v-on:submit.prevent="saveItem"
  >
    <input v-model="newItem" type="text" placeholder="Agregar un articulo" />
    <!--Caja de seleccion de Prioridad-->

    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      Alta Prioridad
    </label>

    <!--Boton-->
    <button class="btn btn-primary">Salvar Articulo</button>

  </form>

  {{ newItemHighPriority }}
  <!-- Lista -->
  <ul>
    <li v-for="item in items" :key="item.id">🛍️ {{ item.label }}</li>
  </ul>
  <p v-if="items.length === 0">🥀NO HAY ELEMENTOS EN TU LISTA 🥀</p>
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>