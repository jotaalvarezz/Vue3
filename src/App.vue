<template>
  <div>
    <h1>{{ name.toUpperCase() }}</h1>
    <br />
    <div class="row" v-for="fruta in arrayFrutas" :key="fruta.id">
      <div class="col-md-12" @click="selectedFruit(fruta)">
        <h2 style="text-decoration: underline;">{{ fruta.name }}</h2>
        <span style="font-weight: bold">{{ fruta.price }}</span>
        <p>{{ fruta.description }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
const name = "Vue 3";
const arrayFrutas = [
  {
    id: 1,
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
  },
  {
    id: 2,
    name: "Pera",
    price: "$2.00",
    description: "Una pera",
  },
  {
    id: 3,
    name: "Naranja",
    price: "$3.00",
    description: "Una naranja",
  },
];

const selectedFruit = (item) => console.log(item.name)

</script>
