<script setup lang="ts">
import { useQRCode } from "@vueuse/integrations/useQRCode";

export type Point = {
  number: string;
  title: string;
};
const props = defineProps<{
  point: Point;
}>();

const apiBase = import.meta.env.VITE_URL_BASE;

// `qrcode` will be a ref of data URL
const qrcode = useQRCode(apiBase + "/espais/" + props.point.number);
</script>
<template>
  <div class="item mb-4">
    <RouterLink :to="'/espais/' + props.point.number" v-if="props.point.title">
      <div class="details text-center">
        <div class="d-flex">
          <div class="number">{{ props.point.number }}</div>
          <h3 class="ms-2 pt-1">{{ props.point.title }}</h3>
        </div>
        <img
          v-if="props.point.title"
          class="h-150"
          :src="qrcode"
          :alt="props.point.title"
        />
        <div v-else class="w-50">
          <img class="h-150" src="@/assets/images/empty.svg" alt="" />
        </div>
      </div>
    </RouterLink>
  </div>
</template>

<style scoped>
.item {
  background: #fff;
  padding: 20px;
  border-radius: 10px 10px 0 0;
}
.item h3 {
  font-weight: 600;
  font-size: 22px;
  color: #003842;
  text-decoration: none;
}
.number {
  border-radius: 50px;
  height: 36px;
  width: 36px;
  background-color: #abd398;
  text-align: center;
  line-height: 36px;
  font-weight: 600;
  font-size: 18px;
  color: #003842;
}
.h-150 {
  height: 165px;
  width: 165px;
  border: 0;
}
</style>
