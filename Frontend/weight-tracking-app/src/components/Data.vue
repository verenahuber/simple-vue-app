<template>
  <div class="container">
    <v-text-field 
      id="input" 
      label="Your Name" 
      v-model="name" 
      size="100%"
      variant="underlined"
    ></v-text-field>
    <v-text-field 
      id="input" 
      label="Your Height" 
      v-model="height" 
      suffix="meters"
      size="100%"
      variant="underlined"
      ></v-text-field>
    <v-text-field 
      id="input" 
      label="Your Age" 
      v-model="age" 
      size="100%"
      variant="underlined"
    ></v-text-field>
    <v-btn @click="changeData">Change</v-btn>
  </div>
</template>

<script>
import axios from "axios"

export default {
  name: "Data",
  data: function () {
    return {
      name: "",
      height: 0,
      age: 0,
      daten: []
    };
  },
  methods: {
    changeData: function () {
      this.$emit("dataChanged", {
        name: this.name,
        height: this.height,
        age: this.age
      });
      axios
      .get("http://localhost:8080/data/").then(response => {
      this.daten = response.data;
    });
      console.log(this.name)
      console.log(this.height)
      console.log(this.age)
    }
  },
  mounted() {
    axios
      .get("http://localhost:8080/data/").then(response => {
      this.daten = response.data;
    });
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  display: flex;
  flex-direction: column;
}
button{
  background-color: #6D60FF;
  border: none;
  color: white;
  padding: 15px 15px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 18px;
  cursor: pointer;
  border-radius: 13px;
  margin: 0;
}
</style>
