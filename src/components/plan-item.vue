<template>
    <div class="plan">
     <div class="description">
        <span class="title"> {{ planIcon }} {{ name }} Precio ${{ price + 100 }}</span>
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
    },
    planIcon: String,
    price: {
        type: Number,
        default: 200
    }
});

</script>

<style scoped> 

</style>