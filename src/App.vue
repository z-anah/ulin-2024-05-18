<template>
    <v-typical class="blink" :steps="['This is a big story short', 1000]" :loop="1" :wrapper="'h2'"></v-typical>
</template>

<script>
import VTypical from 'vue-typical';
export default {
  name: 'App',
  components: {
    VTypical,
  },
}
</script>

<style>
body {
  height: 100vh;
  width: 100vw;
  margin: 0;
  padding: 0;
  background-image: url(./assets/images/wallpaper.jpeg);
  background-size: cover;
  background-position: center;
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
