<template>
  <div v-if="state == 0">
    <Vue3Lottie :animationData="email" :height="80" :width="80" />
    <v-typical class="blink" :steps="['You received a letter', 5000]" :loop="1" :wrapper="'p'"></v-typical>
    <button type="button" v-on:click="to1">Read it!</button>
  </div>
  <div v-if="state == 1">
    <Vue3Lottie :animationData="readysteadygo" :height="80" :width="80" />
    <v-typical class="blink" :steps="['Are you ready?', 5000]" :loop="1" :wrapper="'p'"></v-typical>
    <button type="button" v-on:click="to2">Begin!</button>
  </div>
  <div v-if="state == 2">
    <Vue3Lottie :animationData="cake" :height="80" :width="80" />
    <v-typical class="blink" :steps="['Milad Mubarak Ulin sayang!\nEaaa! Ada yang Ulang Tahun nih!', 5000]" :loop="1"
      :wrapper="'p'"></v-typical>
    <button type="button" v-on:click="to3">Lanjut!</button>
  </div>
  <!-- <div v-if="state == xxx">
    <Vue3Lottie :animationData="xxx" :height="80" :width="80" />
    <v-typical class="blink" :steps="['xxx', 5000]" :loop="1" :wrapper="'p'"></v-typical>
    <button type="button" v-on:click="xxx">xxx</button>
  </div> -->
</template>

<script>
import VTypical from 'vue-typical';
import { Vue3Lottie } from 'vue3-lottie'

import email from './assets/lotties/mail.json'
import readysteadygo from './assets/lotties/ready steady go.json'
export default {
  name: 'App',
  components: {
    Vue3Lottie,
    VTypical
  },
  data() {
    return {
      email,
      readysteadygo,
      state:0,
    }
  },
  methods: {
    to1: function () {
      this.state = 1;
    },
    to2: function () {
      this.state = 2;
    },
    to3: function () {
      this.state = 3;
    }

  }
}
</script>

<style>
body {
  height: 100vh;
  width: 100vw;
  margin: 0;
  padding: 0;
  padding-top: 25vh;
  background-image: url(./assets/images/wallpaper.jpeg);
  background-size: cover;
  background-position: center;
  color: white;
  text-align: center;
  font-family: "Gamer";
}
p{
  font-size: xx-large;
}
@font-face {
  font-family: "Gamer";
  src: url(./assets/fonts/Gamer.ttf);
}

@font-face {
  font-family: "Good-Game";
  src: url(./assets/fonts/Good-Game.ttf);
}

.blink::after {
  content: '|';
  animation: blink 1s infinite step-start;
}

@keyframes blink {
  50% {
    opacity: 0;
  }
}
</style>
