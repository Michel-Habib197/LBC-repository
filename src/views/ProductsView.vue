<template>
  <v-container flat>
    <h1 class="text-decoration-underline d-flex justify-start mb-6 ms-15">Products:</h1>
    <CardsComponent :contents="contents"/>
  </v-container>
</template>
  
<script setup>
import { ref, onMounted } from 'vue';
import CardsComponent from '@/components/CardsComponent.vue';

// const isDrawerOpen = ref(false);
const contents = ref([]);

// const toggleDrawer = () => {
//   isDrawerOpen.value = !isDrawerOpen.value;

// };

onMounted(() => {
  fetch('https://fakestoreapi.com/products')
    .then(res => res.json())
    .then(json => {
      contents.value = json.map(content => ({
        id: content.id,
        img: content.image,
        title: content.title,
        price: content.price,
      }));
    })
    .catch(err => {
      console.error("Erro ao buscar dados da API", err);
    });
});
</script>
