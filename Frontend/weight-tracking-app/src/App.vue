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
  font-family: Montserrat, Helvetica, Arial, sans-serif;
  width: 390px;
}

*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

</style>
