<script setup lang="ts">
import MainTitle from './MainTitle.vue';
import PointItem from './PointItem.vue'
import points from '@/stores/espais';


</script>

<template>
  <MainTitle>Punts<br>d'interés</MainTitle>
  
  <div class="row mt-5">
    <div class="col-12 col-md-4" v-for="point in points" v-key="point.number">
      <PointItem :point="point"></PointItem>
    </div>
  </div>
  
</template>
