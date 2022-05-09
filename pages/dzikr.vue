<template>
  <div>
    <div class="flex items-center px-10 space-x-3 justify-center">
      <img
        :src="require(`~/assets/images/dzikr.png`)"
        alt="dzikr"
        class="h-12 w-12"
      />
      <p class="text-3xl font-medium">Dzikir</p>
    </div>
    <div class="my-5" v-for="(dzikir, id) in dzikirData" :key="id">
      <DzikirCard :dzikir="dzikir" @click="countDzikir(dzikir, audioSound)" />
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
      audioSound: "",
      audioLink:
        "http://soundbible.com/mp3/Air Plane Ding-SoundBible.com-496729130.mp3",
      audioLink1:
        "https://soundbible.com/mp3/Elevator%20Ding-SoundBible.com-685385892.mp3",
    };
  },

  methods: {
    countDzikir(dzikir, sound) {
      this.audioSound = this.audioLink;
      let audio = new Audio(sound);
      if (dzikir.counter + 1 <= 99) {
        audio.play();
        dzikir.counter++;
        if (33 <= dzikir.counter) {
          dzikir.warna = "red";
        }
        if (66 <= dzikir.counter) {
          dzikir.warna = "green";
        }
        if (32 === dzikir.counter) {
          this.audioSound = this.audioLink1;
        }
        if (65 === dzikir.counter) {
          this.audioSound = this.audioLink1;
        }
        if (98 === dzikir.counter) {
          this.audioSound = this.audioLink1;
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
