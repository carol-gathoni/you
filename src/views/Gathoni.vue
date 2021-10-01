<template>
  <div class="ke">
    <kard></kard>
  </div>
</template>

<script>
import kard from "../components/kard.vue";
export default {
  components: { kard },
};
</script>

<style scoped>
.ke {
  margin-left: 155px;
  margin-top: 70px;
}

@media only screen and (max-width: 769px) {
  .ke {
    margin-left: 0px;
  }
}
</style>
