<template>
    <div id="weight">
      <h3>Weight</h3>
      <h2 @click="calculateWeightLoss"> {{ weightCurrent.weight }} kg</h2>
      <p :style="{'color': color}"> {{ result }} kg</p>
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
    box-shadow: 0 3px 10px 0 rgba(0, 0, 0, 0.2);
    border-radius: 13px;
    height: 162px;
    width: 100%;
    background-color: white;
}

h3 {
  font-size: 21px;
  margin-left: -1px;
}

h2 {
  font-size: 33px;
  font-weight: 500;
  margin-top: 20px;
  color: #6D60FF;
  margin-bottom: -3px;
  margin-left: -1px;
}

p {
  font-size: 15px;
  font-weight: 600;
  padding-left: 2px;
}


</style>