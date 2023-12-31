<script setup>
import MonthlyCard from "./MonthlyCard.vue";

const monthlyCardInfos = [
  {
    month: "8월",
    dir: "202308",
    count: 14,
  },
  {
    month: "9월",
    dir: "202309",
    count: 14,
  },
  {
    month: "10월",
    dir: "202310",
    count: 18,
  },
  {
    month: "11월",
    dir: "202311",
    count: 4,
  },
  {
    month: "12월",
    dir: "202312",
    count: 38,
  },
];
</script>

<template>
  <div class="monthly-container">
    <h1>🥖 월별 빵터디 기록 🥖</h1>
    <MonthlyCard
      v-for="cardInfo in monthlyCardInfos"
      :key="cardInfo.month"
      :month="cardInfo.month"
      :dir="cardInfo.dir"
      :count="cardInfo.count"
    ></MonthlyCard>
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

.monthly-container {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
}
</style>
