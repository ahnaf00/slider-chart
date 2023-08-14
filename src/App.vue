<script setup>
import Slider from './components/Slider.vue'
import Chart from './components/Chart.vue'
</script>

<template>
  <div class="mt-10">
    <Slider/>
  </div>

  <div class="chart">
    <Chart/>
  </div>
</template>

<style scoped>
.chart{
  margin-top: 100px;
}
</style>
