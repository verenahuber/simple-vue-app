<template>
  <header> 
    <h3>Weight</h3>
    <h1>History</h1> 
  </header>
  <img src="https://cdn.discordapp.com/attachments/1057666656320618587/1063508237476966450/waage_10.png" >
  <div id="weight_list">
    <ListWeight
      id="ListWeight"
      v-for="(singleEntry, index) of listOfEntries.slice().reverse()"
      :key="index"
      :entry="singleEntry"
      :index="listOfEntries.length - index - 1"
      @weightRemoved="removeWeight"
      @weightEdited="editWeight">
    </ListWeight>
  </div>
</template>

<script>

import ListWeight from "./ListWeight.vue";
import axios from "axios";

export default {
  name: "History",
  props: {
    msg: String
  },
  components: {
    ListWeight
  },
  data: function() {
    return {
      listOfEntries: []
    };
  },
  methods: {
    editWeight: function(e) {
      axios
        .put("http://localhost:8080/weight/" + e.index, {
          weight: e.weight
        })
        .then(response => {
          this.listOfEntries = response.data; 
        });
    },
    removeWeight: function(e) {
      axios
        .delete("http://localhost:8080/weight/" + e.index)
        .then(response => {
        this.listOfEntries = response.data;
      });
    }
  },
  mounted() {
    axios
      .get("http://localhost:8080/weight/").then(response => {
      this.listOfEntries = response.data;
    });
  }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

header {
  position: fixed;
  z-index: 2;
  background-color: #FAFCFE;
  width: 100vh;
  height: 11.5vh;
  left: 0;
  top: 0;
}

h1{
  font-size: 38px;
  font-weight: 500;
  margin-left: 46px;
}

h3{
  margin-bottom: -4px;
  margin-left: 46px;
  margin-top: 35px;
  font-size: 19px;
  color: #AFB0B8;
}

#weight_list {
  margin-top: 112px;
  margin-bottom: 16.4vh;
}

</style>
