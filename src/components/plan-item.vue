<template>
  <div class="plan">
    <div class="description">
      <span class="title"> {{ name }}</span>
    </div>
  </div>
</template>

<script setup>
// Usando un macro para
// definir las props
//defineProps(['name','planIcon']);
defineProps({
  name: {
    tyoe: String,
    required: true
  }
})
</script>

<style scoped>

</style>
