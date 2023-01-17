<template>
  <div class="container" id="welcome">
      <h4>Welcome back</h4>
      <h2> {{ data.name }} </h2>
      <span>Thanks for using our app!</span>
    </div>
  <div class="container">
    <h4 id="headline_data">Personal Data</h4>
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
    <button class="btn" id="btn_change" @click="changeData">Change</button>
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
}
#welcome {
  display: flex;
  flex-direction: column;
  height: 158px;
  width: 100%;
  padding: 20px;
}
h4 {
  font-size: 20px;
  font-weight: 600;
}
h2 {
  font-size: 30px;
  font-weight: 500;
  color: #6D60FF;
  margin-top: 22px;
  margin-bottom: -2px;
}
span {
  font-style: italic;
  color: #A3A5B5;
}
#headline_data {
  margin-bottom: 25px;
}
#btn_change {
  border-radius: 13px;
  margin: 8px -2.5px 0 -2.5px;
  padding: 12px 15px;
}

</style>
