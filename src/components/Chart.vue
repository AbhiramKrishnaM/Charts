<script setup>
import { ref, onMounted } from "vue";
import * as echarts from "echarts";
import heartIcon from "../assets/heart.svg";

const chart = ref(null);

function loadChart() {
  var myChart = echarts.init(chart.value);
  var option;

  option = {
    color: ["#80FFA5", "#00DDFF", "#37A2FF", "#FF0087", "#FFBF00"],
    title: {
      text: "",
    },
    tooltip: {
      trigger: "item",
      backgroundColor: "#fff",
      borderWidth: 0,
      extraCssText:
        "box-shadow: 0px 20px 20px 0px rgba(208, 213, 221, 0.5); border-radius: 8px;",
      textStyle: {
        color: "#333",
      },

      formatter: function (params) {
        return `
    <div id="tooltip" >
      <span style="font-size: 12px; font-weight: 400; color: #70707a">
        ${params.data.date}
      </span>
      <div
        id="value"
        style="
          display: flex;
          align-items: center;
          justify-content: center;
          gap: 6px;
          margin-top: 7px;
          padding: 8px;
          border-radius: 8px;
          background-color: #f4f4f5;
          width: max-content;
        "
      >
        <img src="${heartIcon}" alt="Heart Icon" />
        <p style="font-size: 12px; font-weight: 500; color: #70707a">Score</p>
        <span
          style="
            font-size: 12px;
            font-weight: 500;
            line-height: 19.2px;
            color: #171717;
          "
        >
          ${params.data.value}
        </span>
      </div>
    </div>
  `;
      },

      position: "top",
      axisPointer: {
        type: "none",
      },
    },
    legend: {
      data: [],
    },

    grid: {
      left: "3%",
      right: "4%",
      bottom: "3%",
      containLabel: true,
      // height: "40%",
    },
    xAxis: [
      {
        type: "category",
        boundaryGap: false,
        data: ["Feb 1", "Feb 2", "Feb 3", "Feb 4", "Feb 5", "Feb 6", "Feb 7"],
        splitLine: {
          show: false,
        },
        axisLine: {
          show: false,
        },
        axisTick: {
          show: false,
        },
      },
    ],
    yAxis: [
      {
        show: false,
        type: "value",
        splitLine: {
          show: false,
        },
      },
    ],
    series: [
      {
        name: "Line 5",
        type: "line",
        stack: "Total",
        smooth: true,
        lineStyle: {
          width: 2,
          color: "#16A34A",
        },
        showSymbol: true,
        symbol: "circle",
        symbolSize: 10,
        itemStyle: {
          color: "#16A34A",
          borderColor: "rgba(255, 255, 255)",
          borderWidth: 4,
        },
        label: {
          show: false,
        },
        emphasis: {
          focus: "series",
          itemStyle: {
            color: "#16A34A",
            borderColor: "rgba(255, 255, 255)",
            borderWidth: 4,
          },
        },
        areaStyle: {
          opacity: 0.8,
          color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
            {
              offset: 0,
              color: "rgba(40, 168, 89, 0.2)",
            },
            {
              offset: 1,
              color: "rgba(40, 168, 89, 0)",
            },
          ]),
        },
        data: [
          { value: 220, date: "Tuesday, Feb 1, 2022" },
          { value: 302, date: "Wednesday, Feb 2, 2022" },
          { value: 181, date: "Thursday, Feb 3, 2022" },
          { value: 234, date: "Friday, Feb 4, 2022" },
          { value: 210, date: "Saturday, Feb 5, 2022" },
          { value: 290, date: "Sunday, Feb 6, 2022" },
          { value: 150, date: "Monday, Feb 7, 2022" },
        ],
      },
    ],
  };

  option && myChart.setOption(option);
}

// hooks
onMounted(() => {
  loadChart();
});
</script>

<template>
  <div style="height: 300px">
    <div id="title">
      <span style="font-size: 16px; font-weight: 500; color: #171717">
        Health check progress
      </span>
      <div
        id="percentage"
        style="display: flex; align-items: center; gap: 8px; margin-top: 8px"
      >
        <p
          style="
            background: #dcfce7;
            padding: 8px;
            color: #16a34a;
            border-radius: 100px;
          "
        >
          +23%
        </p>
        <span style="font-size: 14px; font-weight: 400; color: #70707a"
          >vs last month</span
        >
      </div>
    </div>

    <div ref="chart" style="width: 800px; height: 100%"></div>
  </div>
</template>
