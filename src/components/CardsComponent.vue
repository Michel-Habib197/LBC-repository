<template>
    <v-row class="d-flex justify-center">
        <v-col 
        v-for ="content in contents"
        :key="content.id"
        cols="12" lg="3">
            <v-card elevation="16" class="pa-2 bg-white" style="width: 100%; height: 400px">
                <div class="d-flex" style="height: 300px; width: 100%;">
                    <v-img :src="content.img" style="object-fit: contain;"></v-img>
                </div>
                <v-row dense no-gutters class="text-left pa-0 mt-2">
                    <v-col cols="12" style="height: 50px;" class="titulo">
                        <p class="titulo">{{ content.title }}</p>
                    </v-col>
                    <v-col cols="12">
                        <div class="d-flex flex-row">
                            <p class="font-weight-black me-2">Price:</p>
                            <p>${{ content.price }}</p>

                        </div>
                    </v-col>
                </v-row>
            </v-card>
    </v-col>

    </v-row>
</template>

<script setup>
import {defineProps} from 'vue';

const props = defineProps({
    contents:{
        type: Array,
        required: true,
    }
});

</script>

<style scoped>
.titulo {
  overflow: hidden; 
  text-overflow: ellipsis;
  white-space: nowrap;
}
</style>