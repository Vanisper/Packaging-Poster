<script setup lang="ts">
import { ref } from "vue";
import BG1 from "./assets/bg1.jpg";
import BG2 from "./assets/bg2.jpg";
import BGM from "./assets/bgm.ogg";

const bg = ref([
  {
    value: BG1,
    color: "#feee5b"
  }, {
    value: BG2,
    color: "#fe6263"
  },
])

const select = ref(0);
const change = () => {
  select.value = select.value == bg.value.length - 1 ? 0 : select.value + 1
}

</script>

<template>
  <audio controls style="position: fixed;bottom: 0;left: 50%;transform: translateX(-50%);">
    <source :src="BGM" type="audio/ogg">
    Your browser does not support the audio tag.
  </audio>

  <section @click="change" class="main"
    :style="{ backgroundImage: `url(${bg[select].value})`, backgroundColor: bg[select].color }">

  </section>
</template>

<style scoped>
.main {
  height: 100vh;
  width: 100vw;
  background-position: center;
  background-size: auto 100%;
  background-repeat: no-repeat;
}
</style>
