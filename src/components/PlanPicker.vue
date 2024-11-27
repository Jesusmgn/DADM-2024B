<script setup>
import PlanPickerItem from './PlanPickerItem.vue';
import { ref, onMounted, onUnmounted} from 'vue';

// creando una referencia reactiva para el plan seleccionado
const selectedPlan = ref(null);

// lista de planes
const plans = ref(['El cafetero', 'El chelero', 'El intelectual']);

// función que permite almacenar el plan seleccionado
const selectPlan = (name) => {
  // almacenar el plan seleccionado
  selectedPlan.value = name;
};

const plansWrapper = ref(null);

// Intentando obtener la referencia al elemento  .plans
console.log('Termina de ejecutar el script setup😜');

// registrando el hook mounted
onMounted (() => {
console.log("El componente PlanPicker se ha montado 🎉");
console.log(plansWrapper.value);
});

onUnmounted(() => {
  console.log("El componenete planpicker se ha desmontado😘");
});

</script>

<template>
  <div ref="plansWrapper" class="plans">
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