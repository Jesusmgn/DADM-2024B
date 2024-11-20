<template>
  <div @click="selectPlan" class="plan" :class="{ selected: isSelected }">
    <div class="description">
      <!-- Mostrar el título y el emoji si el plan está seleccionado -->
      <span class="title"> {{ name }} {{ isSelected ? '😁' : '' }}</span>
    </div>
  </div>
</template>

<script setup>
// importamos la función para crear una propiedad computada
import { computed } from 'vue';

// Usando un macro para definir las props
const props = defineProps({
  name: {
    type: String,
    required: true
  },
  // Propiedad que indica el plan actualmente seleccionado
  selectPlan: String
});

// Definiendo un evento
const emit = defineEmits(['select']);

// Función que permite cambiar el estado del plan seleccionado
const selectPlan = () => {
  // Emitir el evento para indicar que el plan ha sido seleccionado
  emit('select', props.name);
};

// creamos una propiedad computada para saber si el plan ha sido seleccionado
const isSelected = computed(() => {
  return props.name === props.selectPlan;
});
</script>

<style scoped>

</style>