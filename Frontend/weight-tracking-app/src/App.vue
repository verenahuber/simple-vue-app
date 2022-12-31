<template>
  <div>
   <Navbar/>
   <Home/>
   <History/>
   <Settings/>
   <router-view></router-view>
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import Home from "./components/Home.vue";
import History from "./components/History.vue";
import Settings from "./components/Settings.vue";

export default {
  name: "App",
  components: {
   Navbar,
   Home,
   History,
   Settings
  }
}


</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  
}

*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

</style>
