<script setup>
defineProps(["title", "description", "sub"]);
</script>

<template>
  <div class="card-wrapper">
    <h1>{{ title }}</h1>
    <h2>{{ description }}</h2>
    <h4>{{ sub }}</h4>
  </div>
</template>

<style scoped>
.card-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  max-width: 500px;
  aspect-ratio: 1/1;
  background-image: url("../assets/images/bread.png");
  background-size: 100%;
  background-repeat: no-repeat;

  color: #dc143c;
}
h1,
h2,
h4 {
  font-family: "ONE-Mobile-POP" !important;
}

h1 {
  margin-bottom: 15px;
}

h2 {
  font-size: 45px;
  margin-bottom: 10px;
}
</style>
