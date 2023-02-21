<script setup>
defineProps(["inicio","fin"])

const emit = defineEmits(['next','back'])



</script>
<template>
<div class="btn-group" role="group" aria-label="Basic example">
  <button 
  @click="$emit('back')" 
  type="button" 
  class="btn btn-outline-primary"
  :disabled="inicio===0"
  
  >Previus</button>
 
  <button 
  @click="$emit('next')" 
  type="button" 
  class="btn btn-outline-primary"
  :disabled="fin===100"
  
  >Next</button>
</div>
</template>