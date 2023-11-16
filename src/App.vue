<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HomeView from './views/HomeView.vue';
</script>

<template>
  <main>
    <RouterView />
  </main>

</template>

<style scoped>

main {
  width: 100%;
height: 100vh;
display: flex;

}
</style>
