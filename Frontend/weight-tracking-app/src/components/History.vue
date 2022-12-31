<template>
  <div class="container">
  <p>History</p> 
  </div>
</template>

<script>
export default {
  name: "History",
  props: {
    msg: String
  }
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container{
  height:100vh;
  width:100%;
  background: lightcoral;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 60px;
  color: white;
}

</style>
