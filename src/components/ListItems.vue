<template>
  <div>
    <div
      v-for="(item, index) in items"
      :key="index"
      class="alert alert-primary mt-4"
      role="alert"
      @click="emit('itemFavorito', item.title)"
    >
      <h4 class="alert-heading">{{ item.title }}</h4>
      <p>{{ item.body }}</p>
    </div>
  </div>
</template>

<script setup>
const emit = defineEmits(["itemFavorito"]);

const props = defineProps({
  items: {
    type: Array,
    default: [],
  },
  start:{
    type:Number,
    default: 0
  },
  end:{
    type:Number,
    default:5
  }
});
</script>
