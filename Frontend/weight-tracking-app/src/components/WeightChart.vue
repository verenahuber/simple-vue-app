<template>
    <h3>Statistics</h3>
    <div>
      <Line
      :options="chartOptions"
      :data="chartData"
      />
    </div>
</template>

<script>
  import { Line } from 'vue-chartjs'
  import {
  Chart as ChartJS,
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Tooltip,
  Legend
} from 'chart.js'

  ChartJS.register(Title, Tooltip, Legend, LineElement, CategoryScale, LinearScale, PointElement)

  export default {
    name: 'WeightChart',
    components: { Line },
    data() {
      return {
        chartData: {
          labels: [ 'datum', 'datum', 'datum', 'datum', 'datum', 'datum', 'datum' ],
          datasets: [ { 
            data: [65, 67, 63, 66, 65, 67, 59], 
            label: '7 Days',
            borderColor: '#6D60FF'
          }]
        },
        chartOptions: {
        }
      }
    }
  }
</script>

<style scoped>

h3 {
  font-size: 21px;
  margin-bottom: 30px;
  font-weight: 500;
}

</style>