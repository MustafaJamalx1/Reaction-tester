<template>
  <h1>Reaction timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <p v-if="showResult">reaction time: {{ score }}ms</p>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
</template>

<script>
import Block from "./components/Block.vue";
export default {
  name: "App",
  components: { Block },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: 0,
      showResult: false,
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      console.log(this.delay);
      this.showResult = false;
    },
    endGame(reactiontime) {
      this.score = reactiontime;
      this.showResult = true;
      this.isPlaying = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
