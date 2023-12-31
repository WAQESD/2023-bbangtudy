<script setup>
import NumberView from "./NumberView.vue";
import MapView from "./MapView.vue";
import MonthlyView from "./MonthlyView.vue";
</script>

<template>
  <div class="main-container">
    <h2>2023</h2>
    <h1>🍞 빵터디 🥞</h1>
    <h3>돌아보기</h3>
  </div>
  <NumberView></NumberView>
  <MapView></MapView>
  <MonthlyView></MonthlyView>
</template>

<style scoped>
.main-container {
  display: flex;
  width: 100%;
  height: 100vh;
  flex-direction: column;
  justify-content: center;
}
h1,
h2,
h3 {
  text-align: center;
  line-height: 90px;
}

h1 {
  font-size: 60px;
  margin-bottom: 160px;
  font-family: "seolleimcool-SemiBold" !important;
}

h2 {
  font-size: 80px;
  margin-top: 20px;
  margin-bottom: 10px;
  font-family: "SDSamliphopangche_Outline" !important;
}

h3 {
  font-size: 90px;
  font-family: "ONE-Mobile-POP" !important;
}
</style>
