<script setup>
import PlanPickerItem from './PlanPickerItem.vue';
import { ref } from 'vue';

// creando una referencia reactiva para el plan seleccionado
const selectedPlan = ref(null);

// lista de planes
const plans = ref(['El cafetero', 'El chelero', 'El intelectual']);

// función que permite almacenar el plan seleccionado
const selectPlan = (name) => {
  // almacenar el plan seleccionado
  selectedPlan.value = name;
};
</script>

<template>
  <div class="plans">
    <PlanPickerItem
      v-for="plan in plans" 
      :key="plan" 
      :name="plan"
      :selectPlan="selectedPlan"
      @select="selectPlan" 
    />
  </div>
</template>

<style scoped>
/* Estilos del componente padre (si son necesarios) */
</style>