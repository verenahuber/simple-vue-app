<template>
  <div class="container">
    <p>Home</p> 
  </div>
  <div class="container">
    <AddWeight @weightAdded="addWeight"> </AddWeight>
  </div>
  <div class="container">
    <BMI></BMI>
  </div>
  <div class="container">
    <WeightChart></WeightChart>
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
.container{
  width:100%;
  display: flex;
  font-size: 50px;
  padding: 20px;
}

</style>
