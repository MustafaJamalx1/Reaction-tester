<template>
  <div class="container">
    <h1>Reaction timer</h1>
    <p v-if="!themeChosen">choose ur theme first</p>
    <Themes @theme="handleTheme" v-if="!themeChosen" />
    <button @click="start" :disabled="isPlaying" v-if="themeChosen">
      Play
    </button>
    <p v-if="showResult">reaction time: {{ score }}ms</p>
    <Block
      v-if="isPlaying"
      :delay="delay"
      @end="endGame"
      :imgUrl="{ imgUrl }"
    />
  </div>
</template>

<script>
import Block from "./components/Block.vue";
import Themes from "./components/Themes.vue";

export default {
  name: "App",
  components: { Block, Themes },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: 0,
      showResult: false,
      themeChosen: false,
      imgUrl: 99,
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;

      this.showResult = false;
    },
    endGame(reactiontime) {
      this.score = reactiontime;
      this.showResult = true;
      this.isPlaying = false;
    },
    handleTheme(a) {
      this.imgUrl = a;
      console.log(a);
      this.themeChosen = true;
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
body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-image: linear-gradient(0deg, #d9afd9 0%, #97d9e1 100%);
  background-size: contain;
  background-repeat: no-repeat;
}
.container {
  background-color: #fff;
  width: 50vw;
  height: 50%;
  padding: 50px 0;
  border-radius: 30px;
}
</style>
