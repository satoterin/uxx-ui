<template>
  <div>
    <canvas id="planet-chart"></canvas>
  </div>
</template>

<script>

import Chart from 'chart.js'
import planetChartData from '../main.js'
export default {
    name: 'Chart',
    data() {
        return {
            planetChartData: planetChartData
        }
    },
    mounted() {
        const ctx = document.getElementById('planet-chart');
        new Chart(ctx, this.planetChartData);
    }
}
  
</script>