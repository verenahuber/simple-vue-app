<template>
  <div id="weight_chart">
    <p> WeightChart </p>
    <div>
      <Line
      :options="chartOptions"
      :data="chartData"
      />
    </div>
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

#weight_chart{
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
    padding-left: 15px;
    font-size: 20px;
    box-shadow: 0 5px 10px 0 rgba(0, 0, 0, 0.2);
    border-radius: 13px;
    height: 200px;
    width: 100%;
}


</style>