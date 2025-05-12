<template>
  <div class="btn-group" role="group" aria-label="Basic example">
    <button type="button" class="btn btn-outline-primary" @click="emit('previus')">Anterior</button>
    <button type="button" class="btn btn-outline-primary" @click="emit('next')">Siguiente</button>
  </div>
</template>

<script setup>
const emit = defineEmits(['next','previus'])
</script>
