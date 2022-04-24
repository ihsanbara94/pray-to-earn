<template>
  <div>
    <Navbar />
    <p>Todo List</p>
    <div>
      <input
        type="text"
        :placeholder="`${textInput}`"
        class="px-4 py-2 w-[200px] border-2"
      />
      <Button content="+" />
    </div>
  </div>
</template>

<script>
import Button from "~/components/atoms/Button.vue";
import Navbar from "../components/Navbar.vue";
export default {
  components: { Button, Navbar },
  data() {
    return {
      textInput: "Input Todo",
    };
  },
};
</script>

<style></style>
