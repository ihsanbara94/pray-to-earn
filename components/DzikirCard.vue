<template>
  <div class="rounded border-4 border-sky-500">
    <div class="flex items-center space-x-5 justify-center px-5 py-3">
      <div>
        <p>{{ dzikir.lafaz }}</p>
        <img
          class="w-20 h-12"
          :src="require(`~/assets/images/${dzikir.images}.png`)"
          :alt="`${dzikir.lafaz}`"
        />
      </div>
      <Button content="+" @click="$emit('click', value)" />

      <p class="text-3xl font-medium" :style="`color: ${dzikir.warna}`">
        {{ dzikir.counter }}
      </p>
    </div>
  </div>
</template>

<script>
import Button from "~/components/atoms/Button.vue";
export default {
  components: { Button },
  props: {
    dzikir: {
      type: Object,
      default: () => {},
    },
  },
};
</script>

<style></style>
