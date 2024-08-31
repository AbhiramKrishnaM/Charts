<script setup>
import { ref, onMounted } from "vue";
import * as echarts from "echarts";

const chart = ref(null); // chart reference

function loadChart() {
  var myChart = echarts.init(chart.value);
  var option;

  option = {
    color: ["#80FFA5", "#00DDFF", "#37A2FF", "#FF0087", "#FFBF00"],
    title: {
      text: "",
    },
    tooltip: {
      trigger: "axis",
      backgroundColor: "#fff",
      borderColor: "#ddd",
      borderWidth: 1,
      textStyle: {
        color: "#333",
      },
      position: function (point, params, dom, rect, size) {
        return [
          point[0] - dom.offsetWidth / 2,
          point[1] - dom.offsetHeight - 10,
        ];
      },
      axisPointer: {
        type: "none", // Remove the cross lines
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
      height: "40%",
    },
    xAxis: [
      {
        type: "category",
        boundaryGap: false,
        data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
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
          width: 2, // Line width
          color: "#16A34A", // Line color
        },
        showSymbol: true, // Show symbols
        symbol: "circle", // Symbol type
        symbolSize: 10, // Symbol size
        itemStyle: {
          color: "#16A34A", // Green circle inside
          borderColor: "rgba(255, 255, 255)", // Transparent white border
          borderWidth: 4, // Border width for the circle
        },
        label: {
          show: false, // Hide label on top of points
        },
        emphasis: {
          focus: "series",
          itemStyle: {
            color: "#16A34A", // Same as default color
            borderColor: "rgba(255, 255, 255)", // Transparent white border
            borderWidth: 4, // Border width for hover state
          },
        },
        areaStyle: {
          opacity: 0.8,
          color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
            {
              offset: 0,
              color: "rgba(40, 168, 89, 0.2)", // 20% opacity
            },
            {
              offset: 1,
              color: "rgba(40, 168, 89, 0)", // 0% opacity
            },
          ]),
        },
        data: [220, 302, 181, 234, 210, 290, 150],
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
  <div id="main">
    <div ref="chart" style="width: 800px; height: 500px"></div>
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
