<script setup>
import { RouterView } from 'vue-router'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
</script>

<template>
  <div class="background-image" />
  <div class="content-wrapper">
    <Header />
    <RouterView />
    <Footer />
  </div>
</template>

<style scoped>
.background-image {
  max-width: 1920px;
  position: fixed;
  top: 0;
  width: 100vw;
  height: 100vh;
  margin-top: 0;
  background-image: url('/background.jpeg');
  background-size: cover;
  background-position: center center;
  background-repeat: no-repeat;
  opacity: 0.9;
  z-index: 0;
}
.content-wrapper {
  max-width: 1920px;
  position: relative;
  top: 0;
  z-index: 1;
  padding-top: 0;
  background-color: rgba(0, 0, 0, 0.5);
}
</style>
