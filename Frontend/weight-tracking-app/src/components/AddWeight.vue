<template>
    <div class="container" id="add_weight">
      <h4>Add weight</h4>
      <v-text-field 
        class="mt-1"  
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
  padding: 24px 30px;
  border-radius: 0 13px 13px 0;
}

h4 {
  font-size: 19px;
  font-weight: 600;
  margin-bottom: 32px;
  position: absolute;
}

#label{
  display: flex;
  flex-direction: column;
}

  </style>