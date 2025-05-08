<template>
  <div>
    <h1 class="title">CONTADOR</h1>
    <br />
    <div class="card" style="width: 18rem">
      <div :class="num > 0 ? 'card-body positivo':'card-body negativo'">
        <h1 class="card-title text-dark text-center">{{ num }}</h1>
      </div>
    </div>
    <br />
    <div class="container">
      <div class="row">
        <div class="col-md-12">
          <button class="btn btn-info" @click="contador">Incrementar</button>
        </div>
        <div class="col-md-12 mt-2 mb-2">
          <button class="btn btn-info" @click="restador">Decrementar</button>
        </div>
        <div class="col-md-12">
          <button class="btn btn-info" @click="resetear">Resetear</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const name = "Vue 3";
const num = ref(0);

const contador = () => {
  console.log(num);
  num.value++;
};

const restador = () => {
  num.value--;
};

const resetear = () => {
  num.value = 0;
};
</script>
<style scoped>
.positivo{
  background-color: green;
}

.negativo{
  background-color: red;
}
</style>
