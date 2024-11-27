<script setup>
import PlanPicker from './components/PlanPicker.vue';
import {ref} from 'vue';

const showPlans = ref(false);
</script>

<template>
  <header>
    <div>
      <span id="logo">Liquid Gold Box</span>
      <img src="./assets/logo.png" alt="logo">
    </div>
  </header>

  <div class="content">
    <h1 class="title">Coffee Plans</h1>
    <h2 class="subtitle">
      Viajamos por el mundo para encontrar el mejor café de origen único para ti
    </h2>

    <label><input type="checkbox" v-model="showPlans">
    mostrar selectos de planes
    </label>
    
    <PlanPicker v-if="showPlans" />
    
  </div>
</template>
