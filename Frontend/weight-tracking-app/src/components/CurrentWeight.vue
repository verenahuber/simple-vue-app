<template>
    <div class="container" id="weight">
      <h4>Weight</h4>
      <h2 @click="calculateWeightLoss"> {{ weightCurrent.weight }} kg</h2>
      <span :style="{'color': color}"> {{ result }} kg</span>
    </div>
</template>
  
<script>

export default {
  name: "BMI",
  props: {
    weightCurrent: {
      type: Number,
      required: true,
      default: 10
    },  
    weightOld: {
      type: Number,
      required: true,
      default: 10
    },
  },
  data: function() {
    return {
      result: 'result',
      weightLoss: 0,
      color: ''
    };
  },
  mounted: function() {
    this.calculateWeightLoss();
  },
  updated: function(){
    this.calculateWeightLoss();
  },
  methods: {
    calculateWeightLoss() {
      this.weightLoss = this.weightCurrent.weight - this.weightOld.weight
      if(this.weightCurrent.weight === '' || this.weightOld.weight === '') {
        this.result = 'No Data'
      }
      if(this.weightLoss < 0) {
        this.color = 'green',
        this.result = this.weightLoss
      }else if(this.weightLoss > 0) {
        this.color = 'red'
        this.result = '+' + this.weightLoss
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
  height: 160px;
  width: 100%;
}
h4 {
  font-size: 21px;
  font-weight: 500;
}
h2 {
  font-size: 33px;
  font-weight: 500;
  margin-top: 20px;
  color: #6D60FF;
  margin-bottom: -2px;
  font-weight: 400;
}
span {
  font-size: 15px;
  font-style: italic;
}


</style>