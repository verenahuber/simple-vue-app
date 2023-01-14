<template>
    <header> 
    <h3>Personal</h3>
    <h1>Settings</h1> 
    <img src="https://cdn.discordapp.com/attachments/1057666656320618587/1063508237476966450/waage_10.png" >
  </header>
  <div id="container_settings">
  <Data 
  @dataChanged="changeData"
  :data = daten[0]>
  <!-- :data = daten[0] -->
  </Data>
  <CurrentWeight
    v-if="weightData.length >0"
        :weightCurrent = weightData[weightData.length-1]
        :weightOld = weightData[weightData.length-2]>
  </CurrentWeight>
  
  </div>
  <p> {{ daten[0] }}</p> 
  
</template>

<script>
import Data from "./Data.vue"
import axios from "axios"
import CurrentWeight from "./CurrentWeight.vue";

export default {
  name: "Settings",
  props: {
    msg: String
  },
  data: function() {
    return {
      daten: [],
      weightData: []
    };
  },
  components:{
    Data,
    CurrentWeight
  },
    methods: {
      changeData: function(e) {
        console.log(e.name)
        axios
        .put("http://localhost:8080/data/0" , {
          name: e.name,
          height: e.height,
          age: e.age
        })
    }
    },
    mounted() {
    axios
      .get("http://localhost:8080/data/").then(response => {
      this.daten = response.data;
    });
    axios
      .get("http://localhost:8080/weight/").then(response => {
      this.weightData = response.data;
    });
  }
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

header {
margin-bottom: 30px;
margin-left: 18px;
}
#container_settings {
  margin-bottom: 30vh;
}

h1{
  font-size: 38px;
  font-weight: 500;
}

h3{
  margin-bottom: -4px;
  font-size: 19px;
  color: #AFB0B8;
}


</style>
