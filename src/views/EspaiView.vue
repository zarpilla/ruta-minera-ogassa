<script setup lang="ts">
import MainTitle from '../components/MainTitle.vue';
import points from '@/stores/espais';

import { useRoute } from 'vue-router';
import { computed } from 'vue';

const route = useRoute();
const pointId = computed(() => route.params.id);
const point = computed(() => points.find(p => p.number === pointId.value));
const baseUrl = import.meta.env.VITE_URL_BASE;

</script>
<template>
  <div class="espai text-center">
    <MainTitle v-if="point">{{ point.title}}</MainTitle>
    <div class="row mt-5">
    <div class="col-12 col-md" v-for="audio in point?.audios">
      
      <h2 class="mb-3"> {{ audio.toUpperCase() }}</h2>
      <audio controls class="mb-5">
        <source :src="'/audios/' + point?.number + '-' + audio + '.aac'" type="audio/mpeg">
        Your browser does not support the audio element.
      </audio>
    </div>
  </div>
  </div>
</template>

<style>
audio {
  border-radius: 25px;
}

</style>
