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
  display: flex;
  font-size: 50px;
  padding: 20px;
}

</style>
