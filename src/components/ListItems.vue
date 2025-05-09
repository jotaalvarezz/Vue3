<template>
  <div>
    <div
      v-for="(item, index) in items"
      :key="index"
      class="alert alert-primary mt-4"
      role="alert"
      @click="emit('itemFavorito', item.num)"
    >
      {{ item.label }} - {{ item.num }}
    </div>
  </div>
</template>

<script setup>
const emit = defineEmits(['itemFavorito'])

const props = defineProps({
  items: {
    type: Array,
    default: [],
  },
});
</script>
