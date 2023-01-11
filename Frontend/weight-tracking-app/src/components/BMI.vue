<template>
    <div id="bmi">
      <h1 @click="calculateBmi"> {{ bmi }} </h1>
      <p :style="{'color': color}"> {{ result }} </p>
    </div>
</template>
  
<script>

export default {
  name: "BMI",
  props: ["weight", "height"],
  data: function() {
    return {
      result: 'result',
      bmi: 0,
      color: ''
    };
  },
  methods: {
    calculateBmi() {
      console.log(this.weight, this.height)
      this.bmi = Math.round((this.weight / Math.pow((this.height), 2))*100)/100
      console.log(this.bmi)
      if(this.weight === '' || this.height === '') {
        this.result = 'No Data'
      }

      if(this.bmi < 18.5 && this.bmi > 0) {
        this.result = 'Underweight'
        this.colorData = 'blue'
      }else if(this.bmi >=18.5 && this.bmi < 24.9) {
        this.result = 'Normal'
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