<template>
  <div class="caroline">
    <mytable></mytable>
  </div>
</template>

<script>
import mytable from "../components/mytable.vue";
export default {
  components: {
    mytable,
  },
};
</script>

<style scoped>
.caroline {
  margin-left: 155px;
}
@media only screen and (max-width: 991px) {
  .caroline {
    margin-left: 0px;
  }
}
</style>
