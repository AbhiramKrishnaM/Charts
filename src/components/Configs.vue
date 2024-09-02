<template>
  <div class="config-wrapper">
    <div
      style="
        display: flex;
        align-items: center;
        justify-content: space-between;
        width: 100%;
      "
    >
      <p class="ellipsis">{{ data.title }}</p>
      <img :src="data.trend === 'up' ? Up : Down" alt="Trend icon" />
    </div>

    <Donut
      :percentage="data.percentage"
      :type="data.type"
      :size="130"
      :total="data.total"
      :value="data.value"
      :foregroundColor="data.color"
      backgroundColor="#f9fafb"
    />
  </div>
</template>

<script setup>
import Donut from "./Donut.vue";
import Down from "../assets/Down.svg";
import Up from "../assets/Up.svg";

const props = defineProps({
  data: { type: Object, default: () => {}, required: true },
});
</script>

<style scoped>
.config-wrapper {
  border: 1px solid #e4e4e7;
  width: max-content;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  padding: 24px;
  gap: 12px;
  border-radius: 15.43px;
  width: 255px;
}

.ellipsis {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 165px;
  text-align: center;
}
</style>
