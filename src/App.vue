<template>
  <div v-if="state == 0">
    <Vue3Lottie :animationData="email" :height="80" :width="80" />
    <v-typical :steps="['You received a letter']" :loop="1" :wrapper="'p'"></v-typical>
    <button type="button" v-on:click="to">Read it!</button>
  </div>
  <div v-if="state == 1">
    <Vue3Lottie :animationData="readysteadygo" :height="80" :width="80" />
    <v-typical :steps="['Are you ready?']" :loop="1" :wrapper="'p'"></v-typical>
    <button type="button" v-on:click="to">Begin!</button>
  </div>
  <div v-if="state == 2">
    <Vue3Lottie :animationData="cake" :height="100" :width="100" />
    <v-typical :steps="['Milad Mubarak Ulin sayang!']" :loop="1" :wrapper="'p'"></v-typical>
    <v-typical :steps="[2000, 'Eaaa! Ada yang Ulang Tahun nih!']" :loop="1" :wrapper="'p'"></v-typical>
    <button type="button" v-on:click="to">Lanjut!</button>
  </div>
  <div v-if="state == 3">
    <Vue3Lottie :animationData="moon" :height="100" :width="100" />
    <v-typical class="doa"
      :steps="['Semoga Allah SWT memberkahi setiap langkahmu. Semoga panjang umur, sehat selalu, menjadi pribadi yang lebih baik, lebih bermanfaat lagi untuk banyak orang. Doa terbaik pokonya untuk kamu sayang...']"
      :loop="1" :wrapper="'p'"></v-typical>
    <button type="button" v-on:click="to">Aamiin...</button>
  </div>
  <div v-if="state == 4">
    <Vue3Lottie :animationData="heart" :height="80" :width="80" />
    <v-typical :steps="['Terima kasih telah menjadi bagian dari hidupku.']" :loop="1" :wrapper="'p'"></v-typical>
    <button type="button" v-on:click="to">Lanjut!</button>
  </div>
  <div v-if="state == 5">
    <Vue3Lottie :animationData="stars" :height="80" :width="80" />
    <v-typical :steps="['And again! Happy Level Up Mr Guimauve']" :loop="1" :wrapper="'p'"></v-typical>
    <button type="button" v-on:click="to">Next!</button>
  </div>
  <div v-if="state == 6">
    <Vue3Lottie :animationData="love" :height="80" :width="80" />
    <v-typical :steps="['I love you to the moon and back! Enjoy!']" :loop="1" :wrapper="'p'"></v-typical>
    <button type="button" v-on:click="to">Thank youuu!</button>
  </div>
  <div v-if="state == 7">
    <h1>How long we've been <b>neighbors</b>?</h1>
    <p class="subtitle">October 15, 2022</p>
    <p class="title">{{ daysBetween("2022-10-15") }} days</p>
    <h1>How long we've known <b>each other</b>?</h1>
    <p class="subtitle">November 20, 2023 05:58</p>
    <p class="title">{{ daysBetween("2023-11-20") }} days</p>
    <h1>How long we've been <b>together</b>?</h1>
    <p class="subtitle">April 26, 2024</p>
    <p class="title">{{ daysBetween("2024-04-26") }} days</p>
    <button type="button" v-on:click="to">WOW!</button>
  </div>
  <div v-if="state == 8">
    <v-typical class="title big" :steps="['The End']" :loop="1" :wrapper="'p'"></v-typical>
  </div>
  <div class="bobot">

    <audio ref="audioPlayer" :src="musicSrc" controls></audio>
  </div>
  <!-- <div v-if="state == xxx">
    <Vue3Lottie :animationData="xxx" :height="80" :width="80" />
    <v-typical :steps="['xxx']" :loop="1" :wrapper="'p'"></v-typical>
    <button type="button" v-on:click="to">xxx</button>
  </div> -->
</template>

<script>
import VTypical from 'vue-typical';
import { Vue3Lottie } from 'vue3-lottie'

import email from './assets/lotties/mail.json'
import moon from './assets/lotties/moon.json'
import cake from './assets/lotties/cake.json'
import heart from './assets/lotties/heart.json'
import love from './assets/lotties/love.json'
import stars from './assets/lotties/stars.json'
import readysteadygo from './assets/lotties/ready steady go.json'
import musicSrc from './assets/song.mp3'
export default {
  name: 'App',
  components: {
    Vue3Lottie,
    VTypical
  },
  data() {
    return {
      moon,
      email,
      heart, love, stars,
      readysteadygo,cake,
      state:0,
      dayNeighbors: 0,
      musicSrc
    }
  },
  methods: {
    to: function () {
      this.state++;
      if(this.state==1)this.playMusic();
    },
    daysBetween(date) {
      const givenDate = new Date(date);
      const today = new Date();
      const differenceInMs = today.getTime() - givenDate.getTime();
      const days = Math.floor(differenceInMs / (1000 * 60 * 60 * 24));
      return days;
    },
    playMusic() {
      const audio = this.$refs.audioPlayer;
      if (audio.paused) {
        audio.play();
      } else {
        audio.pause();
      }
    },

  }
}
</script>

<style>
.bobot{
  position: absolute;
    /* Make the div absolutely positioned */
    bottom: 0;
    /* Place it at the bottom of the container */
    right: 0;
}
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
  display: flex;
  justify-content: center;
}
.subtitle{
  font-size: x-large;
  margin-top: -20px;
  color: #e1dada;
}
.doa{
  width: 400px;
}
p{
  font-size: xx-large;
}
.title{
  font-family: 'Good-Game';
  margin-top: -20px;
  }
  .big{
    font-size: 300px;
  }
@font-face {
  font-family: "Gamer";
  src: url(./assets/fonts/Gamer.ttf);
}
b{
  color: #ff7c7c;
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
