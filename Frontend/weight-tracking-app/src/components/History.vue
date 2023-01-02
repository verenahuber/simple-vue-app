<template>
  <div class="container">
    <p>History</p> 
  </div>
  <div class="container"> 
    <ListWeight
      id="ListWeight"
      v-for="(singleEntry, index) of listOfEntries"
      :key="index"
      :entry="singleEntry"
      :index="index"
      @weightRemoved="removeWeight"
      @weightEdited="editWeight"
    ></ListWeight>
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
