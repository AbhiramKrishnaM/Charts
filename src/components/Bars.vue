<template>
  <div style="display: flex; align-items: center; gap: 12px">
    <div
      style="
        width: 26px;
        height: 26px;
        background-color: #f9fafb;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 100%;
      "
    >
      <img :src="Crowdstrike" alt="Crowdstrike" />
    </div>
    <span style="font-size: 14px; font-weight: 400">CrowdStrike</span>
    <div class="progress-container">
      <div class="progress-bar-total">
        <span class="total-value">{{ totalValue }}</span>
      </div>
      <div
        class="progress-bar-active"
        :style="{ width: `${percentage}%`, backgroundColor: activeColor }"
      >
        <span class="active-value">{{ activeValue }}</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from "vue";
import Crowdstrike from "../assets/crowdstrike.png";

const props = defineProps({
  activeValue: {
    type: Number,
    required: true,
  },
  totalValue: {
    type: Number,
    required: true,
  },
  activeColor: {
    type: String,
    default: "#01BAEF", // Color for the active part
  },
  totalColor: {
    type: String,
    default: "#6366F1", // Color for the total part
  },
});

const percentage = computed(() => (props.activeValue / props.totalValue) * 100);
</script>

<style scoped>
.progress-container {
  position: relative;
  width: 403px;
  height: 30px;
  border-radius: 4px;
  overflow: hidden;
  display: flex;
  align-items: center;
  background-color: #e0e0e0; /* Base background color */
}

.progress-bar-total {
  width: 100%;
  height: 100%;
  background-color: #6366f1; /* Base bar color */
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: flex-end;
}

.progress-bar-active {
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  color: white;
}

.total-value {
  position: absolute;
  right: 10px;
  color: #fff;
  font-size: 14px;
  font-weight: 400;
}

.active-value {
  position: absolute;
  right: 10px;
  font-size: 14px;
  font-weight: 400;
  color: #fff;
}
</style>
