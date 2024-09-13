<template>
    <v-app>
      <SideBar :isDrawerOpen="isDrawerOpen" />
      <div>
        <v-app-bar :elevation="0" height="64">
          <v-app-bar-nav-icon class="d-flex" @click="toggleDrawer"></v-app-bar-nav-icon>
        </v-app-bar>
      </div>
      <v-main class>
        <h1 class="text-decoration-underline d-flex justify-start mb-6 ms-15">Table:</h1>
        <div class="table-container">
          <v-data-table
            :items="tableData"
            :headers="headers"
            :loading="loading"
            class="elevation-1"
            height="400px">
            <template v-slot:item="{item}">
                <td>{{ item['Customer Name'] || 'N/A'}}</td>
                <td>{{ item.Sales || 'N/A'}}</td>
                <td>{{ item.City || 'N/A'}}</td>
                <td>{{ item.State || 'N/A'}}</td>
                <td>{{ item.Country || 'N/A'}}</td>
                <td>{{ item['Order Date'] || 'N/A'}}</td>
                <td>{{ item.Category || 'N/A'}}</td>
            </template>
            <template v-slot:no-data>
              <span>Nenhum dado disponível</span>
            </template>
          </v-data-table>
        </div>
     
      </v-main>
    </v-app>
  </template>



  
 <script setup>
 import {ref, watch, onMounted} from 'vue'
 import SideBar from'@/components/SideBar.vue'

 const isDrawerOpen =  ref(false)

 const toggleDrawer=() => {
  isDrawerOpen.value = !isDrawerOpen.value
 }

 const headers = [
  {text:'Name', value:'Customer Name'},
  {text:'Price', value:'Sales'},
  {text:'City', value:'City'},
  {text:'State', value:'State'},
  {text:'Country', value:'Country'},
  {text:'Date of sale', value:'Order Date'},
  {text:'Category', value:'Category'},
 ]

 const tableData = ref([])
 const loading = ref(false)

 const fetchData = async () => {
  try{
    loading.value = true
    const response = await fetch('/StoreSales.json')

    if(!response.ok){
      throw new Error(`Erro: ${response.status} - ${response.statusText}`)
    }

    const data = await response.json()

    if(Array.isArray(data)){
      tableData.value = data.slice(0, 1000)
    }else{
      console.error('Dados carregdos nao sao de uma array', data)
    }

    console.log('Dados carregados:', data)
  }catch(error){
    console.error('Erro o carregar os dados', error)
  }finally{
    loading.value = false
  }
}

onMounted(() => {
  fetchData()
})
</script>

<style scoped>
.table-container {
  height: 400px;
  overflow-y: auto; 
}
</style>