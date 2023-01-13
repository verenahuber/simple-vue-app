<template>
  <div class="container">
    <h3>Your Personal Data</h3>
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
      suffix="years"
      size="100%"
      variant="underlined"
    ></v-text-field>
    <button @click="changeData">Change</button>
  </div>
</template>

<script>

export default {
  name: "Data",
  props: {
    data: {
      type: Promise,
      required: true,
      default: 10
    }
  },
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
  padding: 21px;
  box-shadow: 0 3px 10px 0 rgba(0, 0, 0, 0.2);
  border-radius: 13px;
  width: 100%;
  background-color: white;
}
button{
  background-color: #6D60FF;
  border: none;
  color: white;
  padding: 12px 15px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 18px;
  cursor: pointer;
  border-radius: 13px;
  margin: 8px -2.5px 0 -2.5px;
}
h3 {
  font-size: 21px;
  margin-bottom: 22px;
  margin-left: -1px;
}
</style>
