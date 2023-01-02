<template>
  <div class="container">
  <p>Settings</p>
  </div>
  <div class="container">
  <Data @dataChanged="changeData" ></Data>
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
.container{
  width:100%;
  display: flex;
  font-size: 50px;
  padding: 20px;
}

</style>
