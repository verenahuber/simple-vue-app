<template>
  <header> 
    <h3>Overview</h3>
    <h1>Home</h1> 
  </header>
  <div id="home_container">
  <div id="bmi_weight">
    <CurrentWeight
      :weightCurrent = weightData[weightData.length-1]
      :weightOld = weightData[weightData.length-2]>
      <!--
        :weightCurrent = weightData[weightData.length-1].weight
        :weightOld = weightData[weightData.length-2].weight
      -->
    </CurrentWeight>
    <div id="space" ></div>
    <BMI
      :weight = 79
      :height = 1.73>
      <!-- 
      :weight = weightData[weightData.length-1].weight
      :height = heightData[0].height 
      -->
    </BMI>
  </div>
  <div id="weight_chart">
    <WeightChart
      :label = "[]"
      :chartData = "[]">
      <!-- :label = "label"
      :chartData = "chartData" -->
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
      chartData: []
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
  },
  mounted() {
    axios
      .get("http://localhost:8080/weight/").then(response => {
      this.weightData = response.data;
      for (let i=this.weightData.length-1; i >= this.weightData.length-7; i-- ){
        this.label.push(this.weightData[i].date);
        this.chartData.push(this.weightData[i].weight)
      }
      console.log(this.label)
      console.log(this.chartData)
    });
    console.log('w' + this.weightData)
    axios
      .get("http://localhost:8080/data/").then(response => {
      this.heightData = response.data;
    });
  }
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
  font-size: 21px;
  font-weight: 500;
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
