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
          <ButtonCounter text="Incrementar" :event="contador"/>
        </div>
        <div class="col-md-12 mt-2 mb-2">
          <ButtonCounter text="Decrementar" :event="restador"/>
        </div>
        <div class="col-md-12 mb-2">
          <ButtonCounter text="Resetear" :event="resetear"/>
        </div>
        <div class="col-md-12">
          <ButtonCounter text="Agregar" :disable="setDisable" :event="agregar"/>
        </div>
      </div>
    </div>
    <hr />
    <div class="container" v-if="list.length > 0">
      <div class="row">
        <div class="col-md-6">
          <ListItems :items="list" @itemFavorito="itemFavorito"/>
        </div>
        <div class="col-md-6">
          <span class="text-center">Numero Favorito</span>
          <h1 class="title">{{numeroFav}}</h1>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
import ButtonCounter from "./components/ButtonCounter.vue";
import ListItems from "./components/ListItems.vue";

const num = ref(0);
const numeroFav = ref(0);
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

const itemFavorito = (item) => {
  numeroFav.value = item
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
