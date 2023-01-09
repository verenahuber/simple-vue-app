<template>
  <div class="navbar">
    <div class="nav_buttons">
      <div class="rounded-cicle"><router-link to="/"><v-icon id="icon">mdi-home</v-icon></router-link></div>
      <button id="btn_2"><router-link to="/history"><v-icon>mdi-history</v-icon></router-link></button>
      <button><router-link to="/settings"><v-icon>mdi-account</v-icon></router-link></button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  props: {
    msg: String
  }
  };

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.navbar {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 28px;
  padding: 35px 20px 40px;
  position: fixed;
  bottom: 0;
  width: 100%;
  margin: 0;
  right: 2px;
  background-color: #FAFCFE;
}
.navbar .nav_buttons {
  display: flex;
  align-items: center;
}
.navbar .nav_buttons a {
  padding: 18px 18px;
  margin: 0 5px;
  background: #FAFCFE;
  color: grey;
  cursor: pointer;
  text-decoration: none;
  border-radius: 100px;
}
#btn_2{
  padding-left: 25px;
  padding-right: 25px;
}
.navbar a:hover {
  background-color: #ddd;
  color: black;
}

.active{
  color:#6D60FF !important;
  background: white !important;
  box-shadow: 0 3px 5px 1px rgba(0, 0, 0, 0.2);
}
</style>
