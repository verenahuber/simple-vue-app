<template>
  <div class="container">
    <v-text-field 
      id="input" 
      label="Your Name" 
      v-model="name" 
      size="100%">
    </v-text-field>
    <v-text-field 
      id="input" 
      label="Your Height" 
      v-model="height" 
      suffix="meters"
      size="100%"></v-text-field>
    <v-text-field 
      id="input" 
      label="Your Age" 
      v-model="age" 
      size="100%">
    </v-text-field>
    <v-btn @click="changeData">Change</v-btn>
  </div>
</template>

<script>
export default {
  name: "Data",
  data: function () {
    return {
      height: 0,
      age: 0,
      name: ""
    };
  },
  methods: {
    changeData: function () {
      this.$emit("dataChanged", {
        height: this.height,
        age: this.age
      });
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
</style>
