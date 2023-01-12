<template>
  <div>
   <Navbar></Navbar>
   <router-view></router-view>
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";

export default {
  name: "App",
  components: {
   Navbar
  }
}


</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600&display=swap');

#app {
  font-family: 'Poppins', sans-serif;
  font-weight: 500;
  color: #202020;
  background-color: #FAFCFE;
  padding: 35px 28px 0 28px;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

img {
  position: fixed;
  right: 0;
  margin-right: 50px;
  top: 37px;
  height: 67px;
  z-index: 3;
}


</style>
