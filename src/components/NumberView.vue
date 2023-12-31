<script setup>
import NumberCard from "./NumberCard.vue";

const numCards = [
  { title: "공식 첫 빵터디", description: "2023.08.20", sub: "" },
  { title: "총 빵터디 횟수", description: "23 회", sub: "" },
  { title: "가장 자주 한 달", description: "12월 (7회)", sub: "" },
  { title: "카페 간 최대 거리", description: "15.1km", sub: "꾸드뱅 - 하늘만큼" },
  {
    title: "하루에 간 최대 카페 수",
    description: "4회",
    sub: "하레하레,스타벅스 가수원,스타벅스 갈마,드롭탑",
  },
  { title: "올해 마지막 빵터디", description: "2023.12.28", sub: "" },
];
</script>

<template>
  <div class="number-container">
    <h1 class="number-title">🥨 숫자로 보는 빵터디 🥨</h1>
    <div class="card-container">
      <NumberCard
        v-for="numCard in numCards"
        :key="numCard.title"
        :title="numCard.title"
        :description="numCard.description"
        :sub="numCard.sub"
      ></NumberCard>
    </div>
  </div>
</template>

<style scoped>
h1 {
  padding: 10px;
  font-size: 32px;
  font-family: "seolleimcool-SemiBold" !important;
  margin-bottom: 30px;
  text-align: center;
}

.card-container {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
}
</style>
