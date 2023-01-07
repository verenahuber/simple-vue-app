<template>
    <div id="weight_chart">
      <p> Weight Chart</p>
      <v-sparkline
        :value="test"
        smooth="10"
      ></v-sparkline>
    </div>
</template>
  
<script>
  export default {
    name: "WeightChart",
    data: function() {
    return {
      test: [0, 4, 2, 7, 6, 9, 4, 8, 0, 0, 2, 7, 3, 10, 5]
    };
  },
  };
</script>

<style scoped>

#weight_chart{
    display: flex;
    flex-direction: row;
    margin-bottom: 20px;
    padding-left: 15px;
    font-size: 20px;
    box-shadow: 0 5px 10px 0 rgba(0, 0, 0, 0.2);
    border-radius: 13px;
    height: 200px;
    width: 100%;
}


</style>