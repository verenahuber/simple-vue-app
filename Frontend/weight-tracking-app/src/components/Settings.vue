<template>
    <header> 
    <h3 class="headline_1">Personal</h3>
    <h1 class="headline_2">Settings</h1> 
    <img src="https://cdn.discordapp.com/attachments/1057666656320618587/1063508132757778512/waage_9.png" >
  </header>
  <div class="container_pages">
  <Data 
  @dataChanged="changeData"
  :data = daten[0]>
  <!-- :data = daten[0] -->
  </Data>

  </div>
  
</template>

<script>
import Data from "./Data.vue"
import axios from "axios"

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
  }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


</style>
