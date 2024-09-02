<template>
  <div class="threat-exposure-wrapper">
    <h1 style="font-size: 16px; font-weight: 500; color: #15191e">
      Top Threat Exposures
    </h1>

    <div
      v-for="threat in data"
      :key="threat.id"
      style="
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        gap: 4px;
        padding-bottom: 16px;
        border-bottom: 1px solid #f3f4f6;
        cursor: pointer;
      "
    >
      <span style="font-size: 14px; font-weight: 400; color: #171717">{{
        threat.threat
      }}</span>
      <p style="font-size: 20px; font-weight: 600; color: #dc2626">
        {{ threat.total }}%
      </p>
      <div style="display: flex; align-items: center; gap: 4px">
        <p style="font-size: 14px; font-weight: 500; color: #16a34a">
          {{ threat.remediations }} remediations
        </p>
        <img :src="Link" alt="Link" />
      </div>
    </div>
  </div>
</template>

<script setup>
import Link from "../assets/Link.svg";
const props = defineProps({ data: { type: Array } });
</script>

<style scoped>
.threat-exposure-wrapper {
  padding: 24px;
  border-radius: 16px;
  border: 1px solid #e4e4e7;
  display: flex;
  flex-direction: column;
  gap: 24px;
  max-width: 210px;
}
</style>
