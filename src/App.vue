<template>
  <div>
    <h1 class="title">CONTADOR</h1>
    <br />
    <div class="card" style="width: 18rem">
      <div :class="color">
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
        <div class="col-md-12 mb-2">
          <button class="btn btn-info" @click="resetear">Resetear</button>
        </div>
        <div class="col-md-12">
          <button class="btn btn-info" :disabled="setDisable" @click="agregar()">Agregar</button>
        </div>
      </div>
    </div>
    <hr />
    <div class="container" v-if="list.length > 0">
      <div
        v-for="(item, index) in list"
        @click="actualizar(item)"
        :key="index"
        class="alert alert-primary mt-4"
        role="alert"
      >
        {{ item.label }} - {{ item }}
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

const name = "Vue 3";
const num = ref(0);
const list = ref([
  {
    id: 1,
    label: "uno",
    num: 12,
  },
  {
    id: 2,
    label: "dos",
    num: 26,
  },
  {
    id: 3,
    label: "tres",
    num: 42,
  },
  {
    id: 4,
    label: "cuatro",
    num: 19,
  }
]);

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

const agregar = () => {
  list.value.push({ id:list.value.length, label: "numero", num: num.value });
};

const actualizar = (item) => {
  const index = list.value.findIndex(objeto => objeto.id == item.id)
  console.log(index)
  item.num = 8888
  list[index] = item
}

const color = computed(() => {
  if (num.value < 0) {
    return "negativo";
  }
  return "positivo";
});

const setDisable = computed(() => {
  const verifyNum = list.value.filter(item => item.num === num.value)
  if(verifyNum.length > 0){
    return true
  }
  return false
})
</script>
<style scoped>
.positivo {
  background-color: green;
}

.negativo {
  background-color: red;
}
</style>
