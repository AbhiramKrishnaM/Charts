<script setup>
import Chart from "./components/Chart.vue";
import AssetDiscovery from "./components/AssetDiscovery.vue";
import Configs from "./components/Configs.vue";
</script>

<template>
  <div id="main">
    <Chart />
    <AssetDiscovery />

    <Configs />
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
</style>
