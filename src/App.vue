<template>
  <div id="app">
    <vMainWrapper />
  </div>
</template>

<script>
import vMainWrapper from "./components/v-main-wrapper.vue";

export default {
  name: "app",
  components: {
    vMainWrapper,
  },
};
</script>


<style lang="scss">
@import "~materialize-css/dist/css/materialize.min.css";
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
  font-weight: 700;
}
</style>