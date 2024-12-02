<script setup>
import fancyButton from './components/FancyButton.vue'
</script>

<template>
  <div class="content">
    <fancy-button>
      <template #icon="slotProps">
        ⭐ {{ slotProps }}
      </template>
      Hazme Clic
    </fancy-button>
  </div>
</template>

<style scoped></style>
