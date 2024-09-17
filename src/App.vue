<script setup>
import { RouterView } from 'vue-router'
import SideBar from './components/SideBar.vue';
import { ref } from 'vue';

const isDrawerOpen =  ref(false)
const toggleDrawer=() => {
  isDrawerOpen.value = !isDrawerOpen.value
 }
</script>

<template>
    <v-layout class="rounded rounded-md">
      <SideBar v-model="isDrawerOpen"/>

      <v-app-bar :elevation="0" height="64">
        <v-app-bar-nav-icon class="d-flex" @click="toggleDrawer"></v-app-bar-nav-icon>
      </v-app-bar>


      <v-main class="d-flex align-center justify-center" style="min-height: 300px;">
        <RouterView />
      </v-main>
    </v-layout>
</template>
