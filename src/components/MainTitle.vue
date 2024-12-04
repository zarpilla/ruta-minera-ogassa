<template>
  <div class="itineraries text-center mt-4">
    <img src="@/assets/images/walking.svg" class="walking mt-2 mb-2" alt="" />
    <h2 class="mb-4 mt-2">
      <slot></slot>
    </h2>
    <div class="separa mb-4"></div>
  </div>
</template>
<style lang="css" scoped>
.itineraries h2 {
  text-align: center;
  font-size: 30px;
  font-weight: 600;
  line-height: 32px;
  color: #003842;
}
.separa {
  width: 12vw;
  height: 0px;
  border: 2px solid #49A986;
  margin: auto;
  margin-bottom: auto;  
}
</style>