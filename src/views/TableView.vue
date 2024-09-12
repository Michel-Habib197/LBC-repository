<template>
    <v-app>
      <SideBar :isDrawerOpen="isDrawerOpen" />
      <div>
        <v-app-bar :elevation="0" height="64">
          <v-app-bar-nav-icon class="d-flex" @click="toggleDrawer"></v-app-bar-nav-icon>
        </v-app-bar>
      </div>
      <v-main class="bg-white">
        <h1 class="text-decoration-underline d-flex justify-start mb-6 ms-15">Table:</h1>
          <v-table>
            <thead>
              <tr>
                <th v-for="header in headers" :key="header">

                </th>
              </tr>
            </thead>

            <tbody>
              <tr v-for="data  in tableData" :key="data">
                <th>
                  
                </th>
              </tr>
            </tbody>
          </v-table>
      </v-main>
    </v-app>
  </template>
  
  <script setup>
  import { ref, onMounted }  from 'vue'
  import SideBar from '../components/SideBar.vue'
import { compileStyle } from 'vue/compiler-sfc';

  
  const isDrawerOpen = ref(false)
  const tableData = ref([])
  
  const toggleDrawer = () => {
    isDrawerOpen.value = !isDrawerOpen.value
  }

  onMounted(() => {
    fetch('../StoresSales.json')
    .then(res => res.json())
    .then(json => {
      tableData.value = json.map((venda, index) => {
        /*name = tableData.Product Name
        price = tableData.
        city = tableData.
        state = tableData.
        country = tableData.
        date of sale = tableData.
        category = tableData. */

        if (index < 1000){
          return {
            ...venda,
            City: venda.City.toUppeCase()
        }
      })
    })
  })
  
  
  </script>