<template>
    <v-container fluid>
        <h1 class="text-decoration-underline">Dashboard:</h1>

        <ChartComponent/>
    </v-container>
</template>


<script setup>
import ChartComponent from '@/components/ChartComponent.vue';
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
</script>