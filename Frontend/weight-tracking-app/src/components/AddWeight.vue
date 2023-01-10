<template>
    <div id="add_weight">
      <v-text-field 
        id="input" 
        label="Your Weight today" 
        v-model="weight" 
        size="100%" 
        variant="underlined"

      ></v-text-field>
      <button @click="addWeight">Add</button>
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
          var dateNow = new Date(Date.now())
          var date = dateNow.toString().substr(4, 11)
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

  #add_weight {
    display: flex;
    flex-direction: row;
    margin-bottom: 20px;
    padding-left: 15px;
    font-size: 20px;
    box-shadow: 0 5px 10px 0 rgba(0, 0, 0, 0.2);
    border-radius: 13px;
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
  border-radius: 0 13px 13px 0;
  margin: 0;
}
  </style>