<template>
    <div id="weight">
      <h3>Weight</h3>
      <h2 @click="calculateWeightLoss"> {{ weightCurrent }} kg</h2>
      <p :style="{'color': color}"> {{ weightLoss }} kg</p>
    </div>
</template>
  
<script>

export default {
  name: "BMI",
  props: ["weightCurrent","weightOld"],
  data: function() {
    return {
      weightLoss: 0,
      color: ''
    };
  },
  methods: {
    calculateWeightLoss() {
      this.weightLoss = this.weightCurrent - this.weightOld
      console.log(this.weightLoss)
      if(this.weightCurrent === '' || this.weightOld === '') {
        this.weightLoss = 0
      }
      if(this.weightLoss < 0) {
        this.color = 'green'
      }else if(this.weightLoss > 0) {
        this.color = 'red'
      }
    }
  }
}
</script>

<style scoped>

#weight{
    display: flex;
    flex-direction: column;
    padding: 20px;
    box-shadow: 0 3px 10px 0 rgba(0, 0, 0, 0.2);
    border-radius: 13px;
    height: 162px;
    width: 100%;
    background-color: white;
}

h3 {
  font-size: 21px;
  font-weight: 500;
}

h2 {
  font-size: 33px;
  font-weight: 500;
  margin-top: 20px;
  color: #6D60FF;
  margin-bottom: -4px;
  margin-left: -1px;
}

p {
  font-size: 15px;
  font-weight: 600;
  padding-left: 2px;
}


</style>