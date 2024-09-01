<script setup>
import Chart from "./components/Chart.vue";
import Bars from "./components/Bars.vue";
</script>

<template>
  <div id="main">
    <Chart />
    <Bars :activeValue="20" :totalValue="100" />
  </div>
</template>

<style scoped>
#main {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
