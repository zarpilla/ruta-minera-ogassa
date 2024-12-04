<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <div class="container">
      <div class="d-flex">
      <HelloWorld />      
    </div>
    </div>
  </header>
  <div class="container">
      <RouterView />
    </div>
</template>

<style scoped>
header{
  background: #49A986;
}
nav a{
  color: white;

}
</style>
