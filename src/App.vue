<script setup>
import Chart from "./components/Chart.vue";
import AssetDiscovery from "./components/AssetDiscovery.vue";
import Configs from "./components/Configs.vue";
import ConfigHealth from "./components/ConfigHealth.vue";

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

// Top Vendors Coverage and config health
const topVendorsCoverage = [
  {
    id: 0,
    vendor: "Crowdstrike",
    coverage: { percentage: 23, total: 1000, value: 500, trend: "down" },
    health: { percentage: 50, total: 423, value: 211, trend: "down" },
  },
  {
    id: 1,
    vendor: "Crowdstrike",
    coverage: { percentage: 73, total: 58, value: 58, trend: "up" },
    health: { percentage: 38, total: 213, value: 81, trend: "up" },
  },
  {
    id: 2,
    vendor: "Crowdstrike",
    coverage: { percentage: 63, total: 58, value: 58, trend: "up" },
    health: { percentage: 76, total: 213, value: 81, trend: "up" },
  },
  {
    id: 3,
    vendor: "Crowdstrike",
    coverage: { percentage: 92, total: 58, value: 58, trend: "none" },
    health: { percentage: 69, total: 213, value: 81, trend: "none" },
  },
  {
    id: 4,
    vendor: "Crowdstrike",
    coverage: { percentage: 44, total: 58, value: 58, trend: "down" },
    health: { percentage: 93, total: 213, value: 81, trend: "up" },
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

    <ConfigHealth :data="topVendorsCoverage" />
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
