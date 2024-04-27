<script setup>
  import { RouterView } from 'vue-router'
  import Navbar from './components/Navbar.vue';
  import Footbar from './components/Footerbar.vue';
</script>

<template>
  <Navbar />

  <main>
    <RouterView />
  </main>

  <Footbar />
</template>