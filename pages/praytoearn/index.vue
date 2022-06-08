<template>
  <div>
    <Navbar />
    <div class="flex items-center px-10 space-x-3 justify-center">
      <img
        :src="require(`~/assets/images/pray.png`)"
        alt="dzikr"
        class="h-12 w-12"
      />
      <p class="text-3xl font-medium">Pray To Earn</p>
    </div>
  </div>
</template>
<script>
import Navbar from "~/components/Navbar.vue";
export default {
  components: { Navbar },
};
</script>
<style></style>
