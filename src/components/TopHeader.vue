<template>
  <div class="header">
    <b-navbar toggleable="md" type="dark" variant="secondary">
      <b-navbar-brand href="#">NavBar</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav id="myNav">
          <b-nav-item to="/">Home</b-nav-item>
          <b-nav-item to="/metha">metha</b-nav-item>
          <b-nav-item to="/chair">Chair</b-nav-item>
          <b-nav-item to="/tv">tv</b-nav-item>
          <b-nav-item to="/caroline">Caroline</b-nav-item>
          <b-nav-item to="/gathoni">Gathoni</b-nav-item>
          <b-nav-item to="/gashero">Gashero</b-nav-item>
        </b-navbar-nav>
        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <b-nav-form>
            <b-form-input
              size="sm"
              class="mr-sm-2"
              placeholder="Search"
            ></b-form-input>
            <b-button size="sm" class="my-2 my-sm-0" type="submit"
              >Search</b-button
            >
          </b-nav-form>

          <b-nav-item-dropdown text="Lang" right>
            <b-dropdown-item to="about">about</b-dropdown-item>
            <b-dropdown-item href="#">ES</b-dropdown-item>
            <b-dropdown-item href="#">RU</b-dropdown-item>
            <b-dropdown-item href="#">FA</b-dropdown-item>
          </b-nav-item-dropdown>

          <b-nav-item-dropdown right>
            <!-- Using 'button-content' slot -->
            <template #button-content>
              <em>User</em>
            </template>
            <b-dropdown-item href="#">Profile</b-dropdown-item>
            <b-dropdown-item href="#">Sign Out</b-dropdown-item>
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
#nav a.router-link-exact-active {
  color: white;
}
@media only screen and (min-width: 769px) and (max-width: 1600px) and (-webkit-min-device-pixel-ratio: 1) {
  #nav-collapse {
    display: none;
    padding: 0px;
  }
  #myNav {
    display: none;
    padding: 400px;
  }
}
@media only screen and (min-width: 769px) and (max-width: 1600px) and (-webkit-min-device-pixel-ratio: 1) and (min-resolution: 192dpi) {
  #nav-collapse {
    display: none;
  }
  #myNav {
    display: none;
    padding: 100px;
  }
}

@media only screen and (max-width: 768px) {
  #nav-collapse {
    display: block;
  }
  #myNav {
    display: block;
  }
}
.header {
  z-index: 10;
  position: fixed;
  width: 100%;
  margin-top: 0px;
}
</style>
