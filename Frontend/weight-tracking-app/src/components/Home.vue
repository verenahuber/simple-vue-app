<template>
  <header> 
    <h3>Overview</h3>
    <h1>Home</h1> 
  </header>
  <div>
  <div>
    <BMI></BMI>
  </div>
  <div>
    <WeightChart></WeightChart>
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
import axios from "axios";

export default {
  name: "Home",
  props: {
    msg: String
  },
  components: {
    AddWeight,
    WeightChart,
    BMI
  },
  methods: {
  addWeight: function(e) {
      axios
        .post("http://localhost:8080/weight/", {
          weight: e.weight,
          date: e.date
        })
        .then(response => {
          this.listOfEntries = response.data;
        });
    },
  },
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

header {
margin-bottom: 33px;
margin-left: 13px;
}

h1{
  font-size: 35px;
}

h3{
  margin-bottom: -2px;
  font-size: 18px;
  color: #AFB0B8;
}

</style>
