<template>
    <header> 
    <h3>Personal</h3>
    <h1>Settings</h1> 
  </header>
  <div>
  <div>
  <Data @dataChanged="changeData" ></Data>
  </div>
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
  components:{
    Data
  },
    methods: {
      changeData: function(e) {
        console.log("test")
        axios
        .put("http://localhost:8080/data/0" , {
          height: e.height,
          age: e.age
        })
    },
    }
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

header {
margin-bottom: 33px;
margin-left: 13px;
}

h1{
  font-size: 35px;
}

h3{
  margin-bottom: -2px;
  font-size: 18px;
  color: #AFB0B8;
}

</style>
