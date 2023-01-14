<template>
    <div class="container" id="add_weight">
      <v-text-field 
        class="mt-n1" 
        label="Add today's weight" 
        v-model="weight" 
        size="80%" 
        variant="underlined"
        suffix="kg"
      ></v-text-field>
      <span></span>
      <button class="btn" id="btn_add" @click="addWeight">Add</button>
    </div>
  </template>
  
  <script>
  import BMI from './BMI.vue';

  
  export default {
    name: "AddWeight",
    data: function() {
      return {
        weight: 0,
        date: "",
        disable: false
      };
    },
    methods: {
      addWeight: function() {
        if (this.weight.length > 0) {
          var date = new Date(Date.now()).toLocaleDateString("en-GB")
          this.$emit("weightAdded", {
            weight: this.weight,
            date: date
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
}
#add_weight{
    padding-left: 20px;
    align-items: center;
}
span {
    margin-right: 55px;
}
#btn_add{
  padding: 19px 30px;
  border-radius: 0 13px 13px 0;
}

  </style>