<template>
  <header> 
    <h3>Overview</h3>
    <h1>Home</h1> 
    <img src="https://cdn.discordapp.com/attachments/1057666656320618587/1063508237476966450/waage_10.png" >
  </header>
  <div id="home_container">
  <div id="bmi_weight">
    <CurrentWeight
      v-if="weightData.length >0 && heightData.length >0"
      :weightCurrent = weightData[weightData.length-1]
      :weightOld = weightData[weightData.length-2]>
    </CurrentWeight>
    <div id="space" ></div>
    <BMI
      v-if="weightData.length >0 && heightData.length >0"
      :weight = weightData[weightData.length-1]
      :height = heightData[0]>
    </BMI>
  </div>
  <div id="weight_chart">
    <div id="changeButtons"> 
      <v-btn @click="isweek=true, changeToWeek" class="mx-2">Week</v-btn>
      <v-btn @click="isweek=false, changeToMonth" class="mx-2">Month</v-btn>
    </div>
    <WeightChart
      :isweek="isweek"
      :label="label"
      :weightData="chartDataPrep">
    </WeightChart>
  </div>
  <div>
    <AddWeight @weightAdded="addWeight"> </AddWeight>
  </div>
  </div>
</template>

<script>
import AddWeight from "./AddWeight.vue";
import WeightChart from "./WeightChart.vue";
import BMI from "./BMI.vue";
import CurrentWeight from "./CurrentWeight.vue";
import axios from "axios";


export default {
  name: "Home",
  props: {
    msg: String
  },
  components: {
    AddWeight,
    WeightChart,
    BMI,
    CurrentWeight
  },
  data: function() {
    return {
      weightData: [],
      heightData: [],
      label: [],
      chartDataPrep: [],
      isweek: true
    };
  },
  methods: {
  addWeight: function(e) {
      axios
        .post("http://localhost:8080/weight/", {
          weight: e.weight,
          date: e.date
        })
        .then(response => {
          this.weightData = response.data;
        });
  },
  changeToMonth () {
    console.log(this.isweek);
    let chartData = [];
    let labels = [];
    for (let i=this.weightData.length-30; i <= this.weightData.length-1; i++ ){
      labels.push(this.weightData[i].date);
      chartData.push(this.weightData[i].weight);
      console.log('month')
      console.log(i);
    }
    self.chartDataPrep = chartData;
    self.label = labels;
  },
  changeToWeek () {
    console.log(this.isweek);
    let chartData = [];
    let labels = [];
    for (let i=this.weightData.length-7; i <= this.weightData.length-1; i++ ){
      labels.push(this.weightData[i].date);
      chartData.push(this.weightData[i].weight);
      console.log('week')
      console.log(i);
    }
    self.chartDataPrep = chartData;
    self.label = labels;
  }
  },
  mounted() {
    let self = this;
    axios
      .get("http://localhost:8080/weight/").then(response => {
      this.weightData = response.data;
      let chartData = [];
      let labels = [];
      for (let i=this.weightData.length-(this.isweek ? 7 : 30); i <= this.weightData.length-1; i++ ){
        labels.push(this.weightData[i].date);
        chartData.push(this.weightData[i].weight);
        console.log('mounted');
        console.log(i);
      }
      self.chartDataPrep = chartData;
      self.label = labels;
    });
    axios
      .get("http://localhost:8080/data/").then(response => {
      this.heightData = response.data;
    });
  },
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

header {
margin-bottom: 30px;
margin-left: 18px;
}

#home_container {
  padding-bottom: 40px;
}

h1{
  font-size: 38px;
  font-weight: 500;
}

h3{
  margin-bottom: -4px;
  font-size: 19px;
  color: #AFB0B8;
}

#bmi_weight{
  display: flex;
  flex-direction: row;
  margin-bottom: 30px;
}

#space {
  margin-left: 30px ;
}

#weight_chart {
  margin-bottom: 30px;
  display: flex;
  flex-direction: column;
  padding: 20px;
  box-shadow: 0 3px 10px 0 rgba(0, 0, 0, 0.2);
  border-radius: 13px;
  width: 100%;
  background-color: white;
}
</style>
