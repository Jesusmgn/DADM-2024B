<script setup>
import planItem from './components/plan-item.vue';
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
    <div class="plans">
      <plan-item>El Soltero</plan-item>
      <plan-item>El Curioso</plan-item>
      <plan-item>El Adicto</plan-item>
    </div>
  </div>
</template>
