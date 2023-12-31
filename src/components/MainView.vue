<script setup>
import NumberView from "./NumberView.vue";
import MapView from "./MapView.vue";
import MonthlyView from "./MonthlyView.vue";
</script>

<template>
  <div class="main-container">
    <div class="audio-container">
      <audio autoplay controls>
        <source src="../assets/audio/Shining_Road.mp3" type="audio/mp3" />
      </audio>
    </div>
    <h2>2023</h2>
    <h1>🍞 빵터디 🥞</h1>
    <h3>돌아보기</h3>
  </div>
  <NumberView></NumberView>
  <MapView></MapView>
  <MonthlyView></MonthlyView>
  <div class="main-container">
    <h2>2024</h2>
    <h1 style="margin-bottom: 60px">🍞 빵터디 🥞</h1>
    <h4>새해 복</h4>
    <h4>많이</h4>
    <h4>받으세요</h4>
    <div class="member-container first">대은 | 현정 | 보현</div>
    <div class="member-container last">범수 | 정민 | 재식 | 정현</div>
  </div>
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
h3,
h4 {
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

h4 {
  font-size: 60px;
  font-family: "ONE-Mobile-POP" !important;
}

.member-container {
  width: 100%;
  display: flex;
  justify-content: center;
  font-family: "Orbit-Regular" !important;
  font-size: 18px;
}

.first {
  margin-top: 60px;
}

.last {
  margin-bottom: 60px;
}

.audio-container {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 120px;
}
</style>
