<script setup lang="ts">
import MainTitle from "../components/MainTitle.vue";
import points from "@/stores/espais";

import { useRoute } from "vue-router";
import { computed, ref } from "vue";

const route = useRoute();
const pointId = computed(() => route.params.id);
const point = computed(() => points.find((p) => p.number === pointId.value));
const baseUrl = import.meta.env.VITE_URL_BASE;
const selectedLanguage = ref(0);
</script>
<template>
  <div class="espai text-center">
    <div class="row mt-5">
    <div class="col" v-for="(language, ai) in point?.languages">
        <a
          class="btn mb-4"
          :class="selectedLanguage === ai ? 'selected' : ''"
          @click="selectedLanguage = ai"
        >
          {{ language.toUpperCase() }}
        </a>
      </div>
    </div>

    <MainTitle v-if="point">{{ point.number }}. {{ point.title }}</MainTitle>

    <div class="row mt-5">      
      <div class="text mt-3" v-if="point && point.texts">
        <p v-if="point" v-html="point.texts[selectedLanguage]"></p>

        <audio controls class="mt-3 mb-5" v-if="point?.files">
          <source
            :src="'/audios/' + point?.files[selectedLanguage]"
            type="audio/mpeg"
          />
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
.text {
  font-size: 18px;
}
.btn {
  border-radius: 25px;
  background: var(--senpir-verd-fosc, #003842);
  padding: 12px 20px;
  font-size: 16px;
  font-weight: 600;
  line-height: 17px;
  letter-spacing: 1.5px;
  text-transform: uppercase;
  color: #fff;
  text-decoration: none;
}

@media screen and (min-width: 768px) {
  .btn {
    padding: 12px 30px;
  }
  
}

.btn.selected,
.btn:hover {
  background: var(--senpir-verd-clar, #49a986);
  color: #fff;
}

.text h3 {
  text-align: center;
  font-size: 21px;
  font-weight: 600;
  line-height: 24px;
}
</style>
