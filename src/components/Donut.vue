<template>
  <div class="donut-chart-container">
    <svg :width="size" :height="size" viewBox="0 0 100 100">
      <!-- Background Circle -->
      <circle
        cx="50"
        cy="50"
        :r="radius"
        :stroke="backgroundColor"
        :stroke-width="thickness"
        fill="none"
      />
      <!-- Foreground Circle -->
      <circle
        cx="50"
        cy="50"
        :r="radius"
        :stroke="foregroundColor"
        :stroke-width="thickness"
        :stroke-dasharray="circumference"
        :stroke-dashoffset="offset"
        fill="none"
        transform="rotate(-90 50 50)"
      />
      <!-- Percentage Text -->
      <text
        :x="type === 'secondary' ? 53 : 50"
        :y="type === 'secondary' ? 50 : 55"
        text-anchor="middle"
        alignment-baseline="middle"
        :font-size="fontSize"
        fill="#15191e"
      >
        {{ percentage }}%
      </text>
    </svg>

    <!-- Conditionally rendered div -->
    <div v-if="type === 'secondary'" class="percentage-view">
      {{ value }}/{{ total }}
    </div>
  </div>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps({
  percentage: {
    type: Number,
    required: true,
  },
  type: {
    type: String,
    validator: (value) => ["primary", "secondary"].includes(value),
    required: true,
  },
  size: {
    type: Number,
    default: 100,
  },
  foregroundColor: {
    type: String,
    default: "#01BAEF",
  },
  backgroundColor: {
    type: String,
    default: "#f9fafb",
  },
  fontSize: {
    type: String,
    default: "16px",
  },
  radius: {
    type: Number,
    default: 40,
  },
  total: { type: Number },
  value: { type: Number },
});

const thickness = computed(() => (props.type === "primary" ? 15 : 5));
const circumference = computed(() => 2 * Math.PI * props.radius);
const offset = computed(
  () => circumference.value - (props.percentage / 100) * circumference.value
);
</script>

<style scoped>
.donut-chart-container {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

.percentage-view {
  position: absolute;
  top: 58%;
  left: 37%;
  font-size: 10px;
  font-weight: 400;
  color: #4b5563;
  background-color: #f4f4f5;
  padding: 1.84px 5.53px;
  border-radius: 16.59px;
  border: 0.46px solid #e4e4e7;
}
</style>
