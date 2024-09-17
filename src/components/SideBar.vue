<template>
  <!-- Remova a opção `permanent` e use `:value` para controlar a visibilidade -->
  <v-navigation-drawer  app v-model="model" width="300">
    <v-list>
      <v-list-subheader>Menu</v-list-subheader>
      <v-list-item>
        <div class="d-flex flex-column ms-16">
          <div class="d-flex justify-center ma-6 bg-white rounded">
            <button>Tela 1</button>
          </div>
          <div class="d-flex justify-center ma-6 bg-white rounded">
            <button>Tela 2</button>
          </div>
          <div class="d-flex justify-center ma-6 bg-white rounded">
            <button>Tela 3</button>
          </div>
        </div>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>

</template>

<script setup>
// import { defineProps, watch } from 'vue';

// Recebe a prop `isDrawerOpen` do componente pai
// const props = defineProps({
//   isDrawerOpen: Boolean
// });

// const toggleDrawer = () => {
//   isDrawerOpen.value = !isDrawerOpen.value;
//   console.log("Drawer state:", isDrawerOpen.value); // Debug: verifique o estado do drawer
// };

const model = defineModel()
// watch(() => props.isDrawerOpen, (newVal) => {
//     drawer.value = newVal
//     console.log("Drawer uptaded", drawer.value)
// })
</script>
