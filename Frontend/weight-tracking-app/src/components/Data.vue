<template>
  <div class="container">
    <v-text-field 
      id="input" 
      label="Your Name" 
      v-model="data.name" 
      size="100%"
      variant="underlined"
    ></v-text-field>
    <v-text-field 
      id="input" 
      label="Your Height" 
      v-model="data.height" 
      suffix="meters"
      size="100%"
      variant="underlined"
      ></v-text-field>
    <v-text-field 
      id="input" 
      label="Your Age" 
      v-model="data.age" 
      size="100%"
      variant="underlined"
    ></v-text-field>
    <v-btn @click="changeData">Change</v-btn>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: "Data",
  props: ["data"],
  methods: {
    changeData: function () {
      this.$emit("dataChanged", {
        name: this.data.name,
        height: this.data.height,
        age: this.data.age
      });
      console.log(this.data.name)
      console.log(this.data.height)
      console.log(this.data.age)
    }
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
