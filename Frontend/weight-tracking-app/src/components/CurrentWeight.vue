<template>
    <div id="bmi">
      <h1 @click="calculateWeightLoss"> {{ weightCurrent }} </h1>
      <p :style="{'color': color}"> {{ weightLoss }} </p>
    </div>
</template>
  
<script>

export default {
  name: "BMI",
  props: ["weightCurrent","weightOld"],
  data: function() {
    return {
      weightLoss: 0,
    };
  },
  methods: {
    calculateWeightLoss() {
      this.weightLoss = this.weightCurrent - this.weightOld
      console.log(this.weightLoss)
      if(this.weightCurrent === '' || this.weightOld === '') {
        this.weightLoss = 0
      }
    }
  }
}
</script>

<style scoped>

#bmi{
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