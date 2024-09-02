<script setup>
import Chart from "./components/Chart.vue";
import AssetDiscovery from "./components/AssetDiscovery.vue";
import Configs from "./components/Configs.vue";

// configs data
const configData = [
  {
    id: 0,
    trend: "down",
    title: "Overall Health Summary",
    color: "#FACC14",
    type: "primary",
    total: 20,
    value: 5,
    percentage: 20,
  },
  {
    id: 1,
    trend: "up",
    title: "Configuration Health",
    color: "#16A34A",
    type: "secondary",
    total: 20,
    value: 5,
    percentage: 60,
  },
  {
    id: 2,
    trend: "up",
    title: "Coverage",
    color: "#DC2626",
    type: "secondary",
    total: 20,
    value: 5,
    percentage: 30,
  },
  {
    id: 3,
    trend: "up",
    title: "Human Risk",
    color: "#FACC14",
    type: "secondary",
    total: 20,
    value: 5,
    percentage: 70,
  },
];
</script>

<template>
  <div id="main">
    <Chart />
    <AssetDiscovery />

    <div class="configs-wrapper">
      <Configs :data="config" v-for="config in configData" :key="config.id" />
    </div>
  </div>
</template>

<style scoped>
#main {
  height: 100vh;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
  padding: 16px;
}

.configs-wrapper {
  padding: 24px;
  border-radius: 16px;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 24px;
}
</style>
