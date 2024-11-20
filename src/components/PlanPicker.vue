<script setup>
import PlanPickerItem from './PlanPickerItem.vue';
import { ref, onMounted} from 'vue';

// creando una referencia reactiva para el plan seleccionado
const selectedPlan = ref(null);

// lista de planes
const plans = ref(['El cafetero', 'El chelero', 'El intelectual']);

// función que permite almacenar el plan seleccionado
const selectPlan = (name) => {
  // almacenar el plan seleccionado
  selectedPlan.value = name;
};
// Intentando obtener la referencia al elemento  .plans
console.log('Termina de ejecutar el script setup😜');
console.log(document.querySelector('.plans'));

// registrando el hook mounted
onMounted (() => {
console.log("El componente PlanPicker se ha montado 🎉");
console.log(document.querySelector('.plans'));
});
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