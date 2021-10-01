<template>
  <div id="app">
    <div id="nav">
      <top-header class="navHeader alldiv"></top-header>
      <side-nav class="sideNav alldiv"></side-nav>
      <!--<router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
      -->
    </div>
    <router-view />
  </div>
</template>

<script>
import TopHeader from "@/components/TopHeader.vue";
import SideNav from "@/components/SideNav.vue";

export default {
  components: {
    "top-header": TopHeader,
    "side-nav": SideNav,
  },
};
</script>

<style lang="scss">
@import "~@/assets/scss/vendors/bootstrap-vue/index";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  // text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 1px;
  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #ffffff;
      font-size: 1.2em;
    }
  }
}
.sideNav {
  margin-top: 60px;
}
.alldiv {
  position: relative;
}
</style>





