<script setup>
  import {ref} from 'vue';
  // Modelo
  const header = ref('App lista de compras')
</script>

<template>
  <h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
    </h1>
</template>

<style scoped>
.shopping-cart-icon{
  font-size: 2rem;
}
</style>
