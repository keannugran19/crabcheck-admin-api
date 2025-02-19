<template>
  <Bar :data="data" :options="options" />
</template>

<script lang="js">
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
} from 'chart.js'
import { Bar } from 'vue-chartjs'
import * as barChartConfig from '../graphs/barGraphConfig.js'

ChartJS.register(CategoryScale, LinearScale, BarElement, Title, Tooltip, Legend)

export default {
  name: 'App',
  components: {
    Bar,
  },
  data() {
    return barChartConfig
  },
}
</script>
