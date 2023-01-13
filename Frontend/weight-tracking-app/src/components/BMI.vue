<template>
    <div id="bmi">
      <h3>BMI</h3>
      <h2 @click="calculateBmi"> {{ bmi }} </h2>
      <p :style="{'color': color}"> {{ result }} </p>
    </div>
</template>
  
<script>

export default {
  name: "BMI",
  props: {
    weight: {
      type: Number,
      required: true,
      default: 10
    },  
    height: {
      type: Number,
      required: true,
      default: 10
    },
  },
  data: function() {
    return {
      result: 'result',
      bmi: 0,
      color: ''
    };
  },
  mounted: function() {
    this.calculateBmi();
  },
  updated: function(){
    this.calculateBmi();
  },
  methods: {
    calculateBmi() {
      console.log(this.weight.weight, this.height.height)
      this.bmi = Math.round((this.weight.weight / Math.pow((this.height.height), 2))*100)/100
      console.log(this.bmi)
      if(this.weight.weight === '' || this.height.height === '') {
        this.result = 'No Data'
      }

      if(this.bmi < 18.5 && this.bmi > 0) {
        this.result = 'Underweight'
        this.color = 'red'
      }else if(this.bmi >=18.5 && this.bmi < 24.9) {
        this.result = 'Normalweight'
        this.color = 'green'
      }else if(this.bmi >=24.9 && this.bmi < 29.9) {
        this.result = 'Overweight'
        this.color = 'orange'
      }else if(this.bmi >= 29.9){
        this.result = 'Obesity'
        this.color = 'red'
      }
      console.log(this.result, this.color)
      }
  }
};
</script>

<style scoped>

#bmi{
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
}


</style>