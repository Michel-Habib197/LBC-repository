<template>
    <v-container fluid>
      <h1 class="text-decoration-underline d-flex justify-start ms-5">Table:</h1>
       <v-data-table 
        :items="tableData" 
        :headers="headers" 
        item.value="Product Name" 
       header-class="custom-header"
       ></v-data-table>
    </v-container>
  </template>



  
 <script setup>
 import {ref, onMounted} from 'vue'

 const headers = [
  {title:'Product Name', align: 'start', key:'Product Name'},
  {title: 'Sales', align: 'end', key: 'Sales'},
  {title:'City', align: 'end', key: 'City'},
  {title:'State', align: 'end', key: 'State'},
  {title:'Country', align: 'end', key: 'Country'},
  {title:'Order Date', align: 'end', key: 'Order Date'},
  {title:'Category', align: 'end', key: 'Category'}
 ]

 const tableData = ref([])
 const loading = ref(false)

 const fetchData = async () => {
  try{
    loading.value = true
    const response = await fetch('/StoreSales.json')
    const data = await response.json()

    if(Array.isArray(data)){
      tableData.value = data.slice(0, 1000)
    }else{
      console.error('Dados carregdos nao sao de uma array', data)
    }
  }catch(error){
    console.error('Erro o carregar os dados', error)
  }
}

// const FakeAPI = {
//   async fetch({page, itensPerPage,sortBy}){
//     return new Promise(resolve =>{
//       setTimeout(() => {
//         const start = (page-1)*itensPerPage
//         const end = start + itensPerPage
//         const items = fetchData()

//         if(sortBy.length){
//           const sortKey = sortBy[0].key
//           const sortOrder = sortBy[0].order
//           items.sort((a, b) =>{
//             const aValue = a[sortKey]
//             const bValue = b[sortKey]
//             return sortOrder === 'desc' ? bValue - aValue : aValue - bValue
//           })
//         }
//           const paginated =  items.slice(start,end)
        
//         resolve({items: paginated, total: items.length})
//       }, 500)
//         })
//     }
//   }


onMounted(() => {
  fetchData()
  
})
</script>