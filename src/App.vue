<script setup>
import { ref } from 'vue'
// Modelo
const header = ref('App lista de compras')
// --- items ---
// Item-Model
const items = ref([
  { id: '0', label: '10 bolillos' },
  { id: '1', label: '1 lata frijoles' },
  { id: '2', label: '1 chelas' },
  { id: '3', label: '1 Nutella' }
]);
// Item-Method
const saveItem = () => {
  // Add new item
  items.value.push({id: items.value.length +1, label: newItem.value});
  //clean the input 
  newItem.value = '';
};
const newItem = ref('')
const newItemPriority = ref(false)
</script>

<template>
  <h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
  </h1>
  <!-- Agrupando Entradas de usuario -->
  <form
    class="add-item form"
    v-on:submit.prevent="saveItem">
    <!-- Entrada de texto-->
    <input 
      v-model.trim="newItem" 
      type="text" 
      placeholder="Agregar articulo"/>
    <!-- Radio Buttos -->
    <label>
      <input type="checkbox" value="low" v-model="newItemPriority" />
      Alta Prioridad
    </label>

    <!-- Boton -->
    <button class="btn btn-primary">Salvar Articulo</button>
  </form>
  <!-- Lista -->
  <ul>
    <li v-for="item in items" v-bind:key="item.id">💹 {{ item.label }}</li>
  </ul>
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>
