<template>
  <div>
    <Pie class="h-90" :data="chartData" :options="chartOptions" />
  </div>
</template>

<script>
import { Pie } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, ArcElement } from 'chart.js'

// Register necessary components
ChartJS.register(Title, Tooltip, Legend, ArcElement)

export default {
  components: {
    Pie,
  },
  data() {
    return {
      chartData: {
        datasets: [
          {
            label: 'Crabs',
            data: [12, 19, 3, 5, 2],
            backgroundColor: ['#ff8904', '#432004', '#51a2ff', '#ffdf20', '#9810fa'],
            borderColor: ['#ff8904', '#432004', '#51a2ff', '#ffdf20', '#9810fa'],
            borderWidth: 1,
          },
        ],
        labels: [
          'Cardisoma Carnifex',
          'Scylla Serrata',
          'Portunos Pelagicus',
          'Venitus Latreillei',
          'Metopograpsus Spp',
        ],
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false,
      },
    }
  },
}
</script>

<style></style>
