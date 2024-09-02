<template>
  <div id="asset-discovery-wrapper">
    <div id="main-title">
      <span class="main-title-text">Asset Discovery</span>
      <div class="switch-container">
        <button
          :class="{ active: isActive('device') }"
          @click="setActive('device')"
        >
          Device
        </button>
        <button
          :class="{ active: isActive('user') }"
          @click="setActive('user')"
        >
          User
        </button>
      </div>
    </div>

    <span id="title">Total Devices: {{ total }}</span>

    <div class="device-list">
      <Bar :activeValue="20" :totalValue="100" v-for="i in 4" :key="i" />
    </div>

    <div id="labels">
      <div class="label-item">
        <div class="label-color overlapping"></div>
        <span class="label-text">Overlapping Devices</span>
      </div>
      <div class="label-item">
        <div class="label-color unique"></div>
        <span class="label-text">Unique Devices</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed, ref } from "vue";

import Bar from "./Bars.vue";

const activeButton = ref("device");

const props = defineProps({
  total: { type: Number, default: 100 },
});

const setActive = (button) => {
  activeButton.value = button;
};

const isActive = (button) => activeButton.value === button;
</script>

<style scoped>
#asset-discovery-wrapper {
  padding: 24px;
  border-radius: 16px;
  border: 1px solid #e4e4e7;
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.main-title-text {
  font-size: 16px;
  font-weight: 500;
  color: #15191e;
}

#title {
  font-size: 18px;
  font-weight: 500;
}

.device-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

#labels {
  display: flex;
  align-items: center;
  gap: 16px;
}

.label-item {
  display: flex;
  align-items: center;
  gap: 9px;
}

.label-color {
  width: 12px;
  height: 12px;
  border-radius: 50%;
}

.label-color.overlapping {
  background-color: #01baef;
}

.label-color.unique {
  background-color: #6366f1;
}

.label-text {
  font-size: 14px;
  font-weight: 400;
  color: #9ca3af;
}

#main-title {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.switch-container {
  display: flex;
  align-items: center;
  gap: 12px;
}

.switch-container button {
  padding: 4px 8px;
  cursor: pointer;
  border: none;
  border-radius: 8px;
  background-color: transparent;
  color: #70707a;
  font-size: 14px;
  font-weight: 500;
  transition: background-color 0.3s ease, border 0.3s ease, color 0.3s ease;
}

.switch-container button.active {
  background-color: #f4f4f5;
  border: 1px solid #e4e4e7;
  color: #171717;
}

.switch-container button:not(.active) {
  background-color: transparent;
  border: none;
}
</style>
