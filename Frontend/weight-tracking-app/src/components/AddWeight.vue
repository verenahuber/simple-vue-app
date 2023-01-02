<template>
    <div>
      <v-text-field id="input" label="Your Weight" v-model="weight" size="100%"></v-text-field>
      <v-btn @click="addWeight">Add</v-btn>
    </div>
  </template>
  
  <script>
  export default {
    name: "AddWeight",
    data: function() {
      return {
        weight: 0,
        date: ""
      };
    },
    methods: {
      addWeight: function() {
        if (this.weight.length > 0) {
          this.$emit("weightAdded", {
            weight: this.weight,
            date: ""
          });
          this.weight = 0;
          this.date = "";
        }
      }
    }
  };
  </script>
  <style scoped>
  div {
    display: flex;
    align-items: center;
  }
  </style>