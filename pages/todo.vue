<template>
  <div>
    <div class="flex items-center px-10 space-x-3 justify-center">
      <img
        :src="require(`~/assets/images/todo.png`)"
        alt="dzikr"
        class="h-12 w-12"
      />
      <p class="text-3xl font-medium">Todo List</p>
    </div>
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
export default {
  components: { Button },
  data() {
    return {
      textInput: "Todo",
    };
  },
};
</script>

<style></style>
