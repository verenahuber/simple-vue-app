<template>
  <div>
    <v-text-field id="input" label="Your Height" v-model="height" size="100%"></v-text-field>
    <v-text-field id="input" label="Your Age" v-model="age" size="100%"></v-text-field>
    <v-btn @click="changeData">Change</v-btn>
  </div>
</template>

<script>
export default {
  name: "Data",
  props: ["entry"],
  data: function () {
    return {
      height: 0,
      age: 0
    };
  },
  methods: {
    changeData: function () {
      console.log("1")
      this.$emit("dataChanged", {
        height: this.height,
        age: this.age
      });
      console.log("2")
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div {
  display: flex;
  align-items: center;
}
</style>
