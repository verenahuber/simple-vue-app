<template>
  <div>
   <Navbar/>
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
#app {
  font-family: Roboto, Helvetica, Arial, sans-serif;
  color: #202020;
  background-color: #FAFCFE;
  padding: 35px 28px 0 28px;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

</style>
