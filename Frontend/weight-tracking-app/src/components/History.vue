<template>
  <header> 
    <h3>Weight</h3>
    <h1>History</h1> 
  </header>
  <div>
    <ListWeight
      id="ListWeight"
      v-for="(singleEntry, index) of listOfEntries.slice().reverse()"
      :key="index"
      :entry="singleEntry"
      :index="index"
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
          this.listOfEntries = response.data; //TODO: change this, do not return full list
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
  };
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
