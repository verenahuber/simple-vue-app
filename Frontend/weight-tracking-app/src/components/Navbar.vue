<template>
  <div class="navbar">
    <div class="nav_buttons">
      <v-btn icon="mdi-home" size="x-large" flat>
        <router-link to="/">
          <v-icon size="39" class="ma-n1">mdi-home</v-icon>
        </router-link>
      </v-btn>
      <div id="gap">
      <v-btn icon="history" size="x-large" flat>
        <router-link to="/history">
          <v-icon size="39" class="ma-n1">mdi-history</v-icon>
        </router-link>
      </v-btn>
    </div>
      <v-btn icon="account" size="x-large" flat> 
        <router-link to="/settings">
          <v-icon size="39" class="ma-n1">mdi-account</v-icon>
        </router-link>
      </v-btn>
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
  justify-content: center;
  align-items: center;
  font-size: 28px;
  padding: 27px 0px 40px;
  position: fixed;
  bottom: 0;
  width: 100%;
  margin: 0;
  right: 1.5px;
  background-color: #FAFCFE;
  z-index: 1;
}
.navbar .nav_buttons {
  display: flex;
  align-items: center;
}
.navbar .nav_buttons a {
  padding: 17px;
  background: #FAFCFE;
  color: grey;
  cursor: pointer;
  text-decoration: none;
  border-radius: 100px;
}
#gap{
  padding-left: 30px;
  padding-right: 30px;
}
.active{
  color:#6D60FF !important;
  background: rgb(255, 255, 255) !important;
  box-shadow: 0 3px 10px 0 rgba(0, 0, 0, 0.2);
}
</style>
