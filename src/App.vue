<template>
  <div>
    <ClientList :clientsData="clients" :assigneesData="assignees"/>
  </div>
</template>

<script setup lang="ts">
import ClientList from './components/ClientList.vue'
import { clients, assignees } from "./test-data";
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,200;0,300;0,800;1,600&family=Open+Sans:wght@300&family=Roboto+Slab&display=swap');

body {
  background-color: #EDF2F7;
  font-family: 'Montserrat', sans-serif;
font-family: 'Open Sans', sans-serif;
font-family: 'Roboto Slab', serif;
}
</style>
