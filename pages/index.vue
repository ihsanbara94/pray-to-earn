<template>
  <div>
    <Navbar />
    <Dzikr />
  </div>
</template>

<script>
import Navbar from "../components/Navbar.vue";
import Dzikr from "./dzikr.vue";
export default {
  components: { Navbar, Dzikr },

  data() {
    return {};
  },
};
</script>

<style></style>
