<template>
  <div class="navbar">
    <div class="nav_buttons">
      <div class="btn">Home</div>
      <div class="btn">History</div>
      <div class="btn">Settings</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  props: {
    msg: String
  }
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.navbar{
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 20px;
  padding: 20px 10px;
}

.navbar .nav_buttons{
  display: flex;
  
}
.navbar .nav_buttons .btn{
  padding: 10px 20px;
  margin: 0 10px;
  background: black;
  color: white;
  cursor: pointer;
}

</style>
