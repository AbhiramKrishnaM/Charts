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
