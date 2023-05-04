<template>
  <div class="v-main-wrapper"></div>
  <router-view></router-view>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "v-main-wrapper",
  props: {},
  data() {
    return {
      title: "hello!",
    };
  },
  computed: {
    ...mapGetters(["CART"]),
  },
  methods: {},
  watch: {},
  mounted() {
    console.log("hellooo");
  },
};
</script>

<style>
.v-main-wrapper {
  margin: 0 auto;
  height: 100%;
}
</style>