<template>
  <div>
    <Loading v-if="showLoading" />
    <div class="container" v-else>
      <span class="text-center">FAVORITO</span><br />
      <Paginator @next="next" @previus="previus" />
      <div class="row">
        <div class="col-md-12">
          <ListItems
            :items="list.slice(inicio, fin)"
            :start="inicio"
            :end="fin"
            @itemFavorito="itemFavorito"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";

import ListItems from "./components/ListItems.vue";
import Paginator from "./components/Paginator.vue";
import Loading from "./components/Loading.vue";

const numeroFav = ref("");
const list = ref([]);
const perpage = 10;
const inicio = ref(0);
const fin = ref(perpage);
const showLoading = ref(true);

const itemFavorito = (item) => {
  numeroFav.value = item;
};

const next = () => {
  if (fin.value < list.value.length) {
    inicio.value = inicio.value + perpage;
    fin.value = fin.value + perpage;
  }
};

const previus = () => {
  if (inicio.value > 0) {
    inicio.value = inicio.value - perpage;
    fin.value = fin.value - perpage;
  }
};

onMounted(() => {
  fetchData();
});

/* const fetchData = () => {
  fetch("https://jsonplaceholder.typicode.com/posts")
    .then((res) => res.json())
    .then((data) => {
      console.log(data);
      list.value = data;
    })
    .finally(() => {
      setTimeout(() => {
        showLoading.value = false;
      }, 2000);
    });
}; */

//con async y await

const fetchData = async () => {
  try {
    const res = await fetch("https://jsonplaceholder.typicode.com/posts");
    const data = await res.json();
    list.value = data;
  } catch (error) {
    console.log("error", error);
  } finally {
    setTimeout(() => {
      showLoading.value = false;
    }, 2000);
  }
};
</script>

<style scoped>
.positivo {
  background-color: green;
}

.negativo {
  background-color: red;
}
</style>
