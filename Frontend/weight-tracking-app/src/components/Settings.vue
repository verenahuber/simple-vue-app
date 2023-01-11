<template>
    <header> 
    <h3>Personal</h3>
    <h1>Settings</h1> 
  </header>
  <div>
  <div>
  <Data 
  @dataChanged="changeData"
  :data = daten>
  <!-- :data = daten[0] -->
  </Data>
  </div>
  <p> {{ daten[0] }}</p>
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
      daten: []
    };
  },
  components:{
    Data
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

header {
margin-bottom: 30px;
margin-left: 18px;
}

h1{
  font-size: 38px;
  font-weight: 500;
}

h3{
  margin-bottom: -4px;
  font-size: 21px;
  font-weight: 500;
  color: #AFB0B8;
}


</style>
