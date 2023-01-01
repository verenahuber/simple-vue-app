<template>
  <div class="container">
  <p>Settings</p> 
  </div>
</template>

<script>
export default {
  name: "Settings",
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
  justify-content: center;
  align-items: center;
  font-size: 60px;
}

</style>
