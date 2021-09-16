<template>
  <div id="mySidenav" class="sidenav">
    <b-navbar-nav>
      <b-nav-item to="/metha">metha</b-nav-item>
      <b-nav-item to="/chair">Chair</b-nav-item>
      <b-nav-item to="/tv">tv</b-nav-item>
      <b-nav-item to="/caroline">Caroline</b-nav-item>
      <b-nav-item to="/gathoni">Gathoni</b-nav-item>
      <b-nav-item to="/gashero">Gashero</b-nav-item>
    </b-navbar-nav>
  </div>
</template>

<script>
export default {};
</script>

<style lang="css" scoped>
body {
  font-family: "Lato", sans-serif;
}

.sidenav {
  height: 100%;
  width: 0;
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  background-color: teal;
  overflow-x: hidden;
  transition: 0.5s;
  padding-top: 60px;
  width: 150px;
}

.sidenav a {
  padding: 8px 8px 8px 32px;
  text-decoration: none;
  font-size: 15px;
  color: magenta;
  display: block;
  transition: 0.3s;
}

.sidenav a:hover {
  color: #d8d3d3;
}

@media screen and (max-height: 450px) {
  .sidenav {
    padding-top: 15px;
  }
  .sidenav a {
    font-size: 18px;
  }
}

@media only screen and (min-width: 991px) and (max-width: 1600px) and (-webkit-min-device-pixel-ratio: 1) {
  .sidenav {
    display: block;
  }
}
@media only screen and (min-width: 991px) and (max-width: 1600px) and (-webkit-min-device-pixel-ratio: 1) and (min-resolution: 192dpi) {
  .sidenav {
    display: block;
  }
}

@media only screen and (max-width: 991px) {
  .sidenav {
    display: none;
  }
}
</style>
