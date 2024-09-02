<template>
  <div class="config-health-wrapper">
    <h1 style="font-size: 16px; font-weight: 500; color: #15191e">
      Top Vendors Coverage & Config Health
    </h1>

    <table>
      <thead>
        <tr>
          <th
            style="
              text-align: start;
              font-size: 12px;
              font-weight: 500;
              color: #9ca3af;
            "
          >
            Vendor
          </th>
          <th
            style="
              text-align: start;
              font-size: 12px;
              font-weight: 500;
              color: #9ca3af;
            "
          >
            Coverage
          </th>
          <th
            style="
              text-align: start;
              font-size: 12px;
              font-weight: 500;
              color: #9ca3af;
            "
          >
            Config Health
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="topVendor in props.data" :key="topVendor.vendor">
          <td style="display: flex; align-items: center; gap: 16px">
            <div class="device-icon">
              <img :src="Crowdstrike" alt="Crowdstrike" />
            </div>
            <span class="device-name">CrowdStrike</span>
          </td>
          <td>
            <div style="display: flex; align-items: center; gap: 8px">
              <span
                style="font-size: 18px; font-weight: 600"
                :class="getTextColorClass(topVendor.coverage.percentage)"
              >
                {{ topVendor.coverage.percentage }}%
              </span>

              <img
                :src="
                  topVendor.coverage.trend === 'none'
                    ? None
                    : topVendor.coverage.trend === 'up'
                    ? Up
                    : Down
                "
                alt="Trend icon"
              />
            </div>

            <div
              style="
                font-size: 12px;
                font-weight: 400;
                color: #9ca3af;
                margin-top: 8px;
              "
            >
              ({{ topVendor.coverage.value }}/{{ topVendor.coverage.total }})
            </div>
          </td>
          <td>
            <div style="display: flex; align-items: center; gap: 8px">
              <span
                style="font-size: 18px; font-weight: 600"
                :class="getTextColorClass(topVendor.health.percentage)"
              >
                {{ topVendor.health.percentage }}%
              </span>

              <img
                :src="
                  topVendor.health.trend === 'none'
                    ? None
                    : topVendor.health.trend === 'up'
                    ? Up
                    : Down
                "
                alt="Trend icon"
              />
            </div>

            <div
              style="
                font-size: 12px;
                font-weight: 400;
                color: #9ca3af;
                margin-top: 8px;
              "
            >
              ({{ topVendor.health.value }}/{{ topVendor.health.total }})
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import Crowdstrike from "../assets/crowdstrike.png";
import Down from "../assets/Down.svg";
import Up from "../assets/Up.svg";
import None from "../assets/None.svg";

const props = defineProps({
  data: { type: Array, required: true },
});

function getTextColorClass(percentage) {
  if (percentage > 0 && percentage < 50) {
    return "red";
  } else if (percentage >= 50 && percentage < 70) {
    return "orange";
  } else {
    return "green";
  }
}
</script>

<style scoped>
.config-health-wrapper {
  padding: 24px;
  border-radius: 16px;
  border: 1px solid #e4e4e7;
  display: flex;
  flex-direction: column;
  gap: 24px;
  height: max-content;
  max-width: 422px;
}

table {
  width: 100%;
  border-collapse: collapse; /* Ensures border and spacing are handled properly */
}

th,
td {
  padding: 8px; /* Adds padding inside cells */
}

tr {
  display: table-row;

  font-size: 14px;
  font-weight: 400;
}

.device-icon {
  width: 36px;
  height: 36px;
  background-color: #f9fafb;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
}

.device-name {
  font-size: 14px;
  font-weight: 400;
}

.green {
  color: #16a34a;
}

.red {
  color: #dc2626;
}

.orange {
  color: #facc14;
}
</style>
