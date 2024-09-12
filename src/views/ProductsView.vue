<template>
    <v-app>
        <SideBar :isDrawerOpen="isDrawerOpen"/>
      <div>
        <v-app-bar :elevation="0" height="64">
        <v-app-bar-nav-icon class="d-flex " @click="toggleDrawer"></v-app-bar-nav-icon>
        </v-app-bar>
      </div>
     
      
      <v-main class="bg-white">
   
        <h1 class="text-decoration-underline d-flex justify-start mb-6 ms-15">Products:</h1>
        <v-container flat>
          <CardsComponent :contents="contents"/>
        </v-container>
      </v-main>
    </v-app>
  </template>
  
<script setup>
import { ref, onMounted } from 'vue';
import SideBar from '../components/SideBar.vue';
import CardsComponent from '@/components/CardsComponent.vue';

const isDrawerOpen = ref(false);
const contents = ref([]);

const toggleDrawer = () => {
  isDrawerOpen.value = !isDrawerOpen.value;

};

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
