<template>
  <div class="navbar">
    <div class="nav_buttons">
      <div class="btn"><router-link to="/">Home</router-link></div>
      <div class="btn"><router-link to="/history">History</router-link></div>
      <div class="btn"><router-link to="/settings">Settings</router-link></div>
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
.navbar {
  background-color: rgba(255, 255, 255, 0.8);
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 20px;
  padding: 40px 20px;
  position: fixed;
  bottom: 0;
  width: 100%;
  margin: 0;
  right: 2px;
}
.navbar .nav_buttons {
  display: flex;
  align-items: center;
}
.navbar .nav_buttons a {
  padding: 18px 18px;
  margin: 0 5px;
  background: lightgray;
  color: white;
  cursor: pointer;
  text-decoration: none;
  border-radius: 100px;
}

.navbar a:hover {
  background-color: #ddd;
  color: black;
}

.active{
  color:#6D60FF !important;
  background: white !important;
  border: 2px solid #6D60FF;
}

</style>
