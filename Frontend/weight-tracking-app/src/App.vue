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
  font-weight: 400;
  color: #202020;
  background-color: #FAFCFE;
  padding: 35px 28px 0 28px;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

header {
  position: fixed;
  z-index: 2;
  background-color: #FAFCFE;
  width: 100vw;
  height: 138px;
  left: 0;
  top: 0;
}

.headline_1{
  font-weight: 500;
  margin-bottom: -5px;
  margin-left: 44px;
  margin-top: 35px;
  font-size: 21px;
  color: #AFB0B8;
}

.headline_2{
  font-size: 38px;
  font-weight: 500;
  margin-left: 43px;
}

.head_image {
  position: fixed;
  right: 0;
  margin-right: 47px;
  top: 52px;
  height: 50px;
}

.container_pages {
  margin-top: 112px;
  margin-bottom: 17.2vh;
}

.container {
  box-shadow: 0 3px 8px 0 rgba(0, 0, 0, 0.2);
  border-radius: 13px;
  background-color: white;
  margin-bottom: 28px;
}

.btn {
  background-color: #6D60FF;
  border: none;
  color: white;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 17.5px;
  cursor: pointer;
  margin: 0;
}

.btn:active {
  background-color: #7c70fc;
}


</style>
