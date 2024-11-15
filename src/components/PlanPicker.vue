<script setup>
import PlanPickerItem from './PlanPickerItem.vue';
import { ref } from 'vue';
//Creando una Referencia reactiva 
// para almacenar el plan seleccionado
const selectedPlan = ref(null);
const plans = ref(['El cafetero', 'El chelero', 'El intelectual']);
const selectPlan = (name) => {
  // Almacenar el plan seleccionado
  selectedPlan.value = name;
}
</script>

<template>
  <div class="plans">
    <PlanPickerItem
     v-for="plan in plans" 
     :key="plan" 
     :name="plan"
     @select="selectPlan"
     :select-plan="selectPlan"></PlanPickerItem>
  </div>
  <p> {{ selectedPlan }} </p>
</template>

<style scoped></style>
