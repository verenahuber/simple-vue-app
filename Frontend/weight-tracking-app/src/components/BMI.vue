<template>
    <div id="bmi">
      <p> BMI funkt noch nicht 100% bitte nichts verändern:)</p>
      <!-- <p> {{ weightData[weightData.length-1] }} </p>
      <p> {{ heightData[0] }} </p> -->
      <p> {{ bmiBerechnen }}</p>
    </div>
</template>
  
<script>
import axios from "axios"

export default {
  name: "BMI",
  data: function() {
    return {
      weightData: [],
      heightData: []
    };
  },
  methods: {
    bmiBerechnen: function(){
      if (heightData[0].height && weightData[weightData.length-1].weight != 0){
        var bmi = weightData[this.weightData.length-1].weight / Math.pow(heightData[0].height, 2);
        return bmi
      } else {
        const fehler = "not enough data";
        return fehler
      }
    }
  },
  mounted() {
    axios
      .get("http://localhost:8080/data/").then(response => {
      this.heightData = response.data;
    });
    axios
      .get("http://localhost:8080/weight/").then(response => {
      this.weightData = response.data;
    });
  }
}
</script>

<style scoped>

#bmi{
    display: flex;
    flex-direction: row;
    margin-bottom: 20px;
    padding-left: 15px;
    font-size: 20px;
    box-shadow: 0 5px 10px 0 rgba(0, 0, 0, 0.2);
    border-radius: 13px;
    height: 200px;
    width: 100%;
}


</style>