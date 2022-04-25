<template>
  <div>
    <div class="flex items-center px-10 space-x-3 justify-center">
      <img :src="require(`~/static/dzikr.png`)" alt="dzikr" class="h-12 w-12" />
      <p class="text-3xl font-medium">Dzikir</p>
    </div>
    <div class="my-5" v-for="(dzikir, id) in dzikirData" :key="id">
      <DzikirCard :dzikir="dzikir" @click="countDzikir(dzikir)" />
    </div>
    <Button style="float: right" content="Reset" @click="resetFcn()" />
  </div>
</template>

<script>
import Button from "../components/atoms/Button.vue";
import DzikirCard from "../components/DzikirCard.vue";
export default {
  components: { DzikirCard, Button },
  data() {
    return {
      dzikirData: [
        {
          lafaz: "Astaghfirullah",
          counter: 0,
          images: "istighfar",
          warna: "blue",
        },
        {
          lafaz: "Subhanallah",
          counter: 0,
          images: "subhanallah",
          warna: "blue",
        },
        {
          lafaz: "Alhamdulillah",
          counter: 0,
          images: "alhamdulillah",
          warna: "blue",
        },
        {
          lafaz: "Lailahaillallah",
          counter: 0,
          images: "lailaha",
          warna: "blue",
        },
        {
          lafaz: "Allahuakbar",
          counter: 0,
          images: "allahuakbar",
          warna: "blue",
        },
      ],
      detailDzikir: {},
    };
  },
  methods: {
    countDzikir(dzikir) {
      this.detailDzikir = dzikir;
      if (this.detailDzikir.counter + 1 <= 99) {
        this.detailDzikir.counter++;
        if (33 <= this.detailDzikir.counter) {
          this.detailDzikir.warna = "red";
        }
        if (66 <= this.detailDzikir.counter) {
          this.detailDzikir.warna = "green";
        }
      }
    },
    resetFcn() {
      let i;
      for (i = 0; i <= this.dzikirData.length - 1; i++) {
        this.dzikirData[i].counter = 0;
        this.dzikirData[i].warna = "blue";
      }
    },
  },
};
</script>

<style></style>
