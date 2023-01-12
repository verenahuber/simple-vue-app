<template>
    <div id="add_weight">
      <v-text-field 
        id="input" 
        class="mt-n1" 
        label="Add today's weight" 
        v-model="weight" 
        size="80%" 
        variant="underlined"
        suffix="kg"
      ></v-text-field>
      <span id="p2"></span>
      <button @click="addWeight">Add</button>
    </div>
  </template>
  
  <script>
  
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
    display: flex;
    flex-direction: row;
    margin-bottom: 20px;
    padding-left: 20px;
    box-shadow: 0 3px 10px 0 rgba(0, 0, 0, 0.2);
    border-radius: 13px;
    align-items: center;
    background-color: white;
}

#p2 {
    margin-right: 55px;
    color: grey;
}

#input {
    width: 100px;
}

button{
  background-color: #6D60FF;
  border: none;
  color: white;
  padding: 19px 30px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 18.5px;
  font-weight: 400;
  cursor: pointer;
  border-radius: 0 13px 13px 0;
  margin: 0;
}

  </style>