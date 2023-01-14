<template>
  <div class="container">
    <h4>Your Personal Data</h4>
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
#btn_change{
  padding: 12px 15px;
  border-radius: 13px;
  margin: 8px -2.5px 0 -2.5px;
}
h4 {
  font-size: 21px;
  font-weight: 500;
  margin-bottom: 23px;
}

</style>
