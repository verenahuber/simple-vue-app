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
    props: {
      label: {
        type: Array,
        required: true,
        default: []
      },  
      weightData: {
        type: Array,
        required: true,
        default: []
      },
    },
    data() {
      return {
        chartData: {
          labels: this.label,
          datasets: [ { 
            data: [...this.weightData], 
            label: '7 Days',
            borderColor: '#6D60FF'
          }]
        },
        chartOptions: {
        }
      }
    },
    mounted() {
      this.updateChart();
    },
    updated() {
      this.updateChart();
    },
    methods: {
      updateChart() {
      this.chartData =  {
          labels: this.label,
          datasets: [ { 
            data: [...this.weightData], 
            label: '7 Days',
            borderColor: '#6D60FF'
          }]
        };
        console.log("UPDATE" ,this.chartData)
      }
    }
  }
</script>

<style scoped>

h3 {
  font-size: 21px;
  margin-bottom: 30px;
  margin-left: -1px;
}

</style>