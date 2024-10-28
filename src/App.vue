<script setup>
import { ref, computed } from 'vue'
// Modelo
const header = ref('App lista de compras')

// --- items ---
// Item-Model
const items = ref([
  { id: '0', label: '10 bolillos', purchased: true, priority: true },
  { id: '1', label: '1 lata frijoles', purchased: true, priority: true },
  { id: '2', label: '1 chelas', purchased: false, priority: false },
  { id: '3', label: '1 Nutella', purchased: false, priority: true }
]);

// Item-Method
const saveItem = () => {
  // Add new item
  items.value.push({ 
    id: items.value.length + 1, 
    label: newItem.value ,
    highPriority: newItemPriority.value
  });
  //clean the input
  newItem.value = '';
  newItemPriority.value = false;
};

// Funcion que alterna el valor de la variable editing
const doEdit = (edit) => {
  editing.value = edit;
  //Limpiando la entrada de texto
  // en caso de que se oculte o muestre
  // el formulario
  newItem.value = "";
  newItemPriority.value = false;
}
// --- Formulario ---
const newItem = ref('')
const newItemPriority = ref(false)
const editing = ref(false)
const activateEdition = (activate) => {
  editing.value = activate
}

//--Colocando una hyperlink con metodo --
/* const goGoogle = () => {
  if (newItem.value.length) return https://${newItem.value};
  return 'https://google.com';
} */

// Alternando estado de compra del item
const togglePurchased = (item) => {
  item.purchased = !item.purchased;
};

//Creando una Propiedad computada 
const characterCount = computed (() => {
  // Toda propiedad computada debe regresar un valor 
  return newItem.value.length;
});

//Creando propiedad computada que invierte items de la lista 
const reversedItems = computed (() => {
  return [items.value].reverse();
});
</script>

<template>
  <div class="heder">
    <h1>
      <i class="material-icons shopping-cart-icon"> local_mall </i>
      {{ header }}
    </h1>
    <button v-if="editing" class="btn" @click="activateEdition(false)">Cancelar</button>
    <button v-else class="btn btn-primary" @click="activateEdition(true)">Agregar Articulo</button>
  </div>
  <!--Colocando una hyperlink-->
  <!-- <a :href=goGoogle()>{{ newItem === '' ? '🔗 LINK' : newItem}}</a> -->
  <!-- <a v-bind:href= "newItem == '' ? 'https://www.google.com' : 'http://' + newItem" target="_blank">
    {{newItem == "" ? "🔗 Link" : newItem }}
  </a> -->

  <!-- Agrupando Entradas de usuario  -->
  <form class="add-item form" v-if="editing" v-on:submit.prevent="saveItem">
    <!-- Entrada de texto-->
    <input v-model.trim="newItem" type="text" placeholder="Agregar articulo" />
    <!-- Radio Buttos -->
    <label>
      <input type="checkbox" value="low" v-model="newItemPriority" />
      Alta Prioridad
    </label>

    <!-- Boton -->
    <button :disabled="newItem.length === 0" class="btn btn-primary">Salvar Articulo</button>

    <!-- Contador -->
   <p class="counter">
    {{ characterCount }} /200
   </p>

  </form>

  <!-- Lista -->
  <ul>
    <li
      v-for="({ id, label, purchased, Priority }, index) in reversedItems"
      :class="{ strikeout: purchased, priority: Priority}"
      @click="togglePurchased(reversedItems[index])"
      v-bind:key="id">
      {{ priority ? '🔥' : '🛍' }} {{ label }}
    </li>
  </ul>
  <!-- Lista clases como arreglos -->
  <ul>
    <li
      v-for="{ label, id, purchased, priority } in items"
      v-bind:key="id"
      :class="[purchased ? 'strikeout' : '' , priority ? 'priority' : '']">
      {{ priority ? '🔥' : '🛍' }} {{ label }}
    </li>
  </ul>
  <p v-if="items.length === 0">🥀 NO HAY ELEMENTOS EN TU LISTA 🥀</p>
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>
