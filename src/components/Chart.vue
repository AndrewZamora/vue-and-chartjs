<template>
  <canvas ref="chart"></canvas>
</template>

<script>
import Chart from "chart.js";
export default {
  data() {
    return {
      chart: null
    };
  },
  props: ["data"],
  mounted() {
    this.chart = new Chart(this.$refs.chart, this.data);
  },
  computed: {
    dataSets() {
      return this.data.datasets;
    }
  },
  watch: {
    dataSets(newDatasets, oldDatasets) {
      if (newDatasets !== oldDatasets) {
        this.chart.data.datasets = newDatasets;
        this.chart.update();
      }
    }
  }
};
</script>

<style>
</style>
