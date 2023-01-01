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
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 20px;
  padding: 20px 10px;
}

.navbar .nav_buttons {
  display: flex;
  
}
.navbar .nav_buttons a {
  padding: 10px 20px;
  margin: 0 10px;
  background: black;
  color: white;
  cursor: pointer;
  text-decoration: none;
}

.active{
  color:red !important;
  background: white !important;
  border: 1px solid black;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

</style>
