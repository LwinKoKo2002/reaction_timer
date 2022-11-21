<template>
  <h1>How fast can you catch me?</h1>
  <button @click="clickHandler" :disabled="isPlaying">Play</button>
  <div v-if="isPlaying">
    <ClickBlock :delay="delay" @endGame="endGame" />
  </div>
  <div v-if="end">
    <ResultScore :score="score" />
  </div>
</template>

<script>
import ResultScore from "./components/ResultScore.vue";
import ClickBlock from "./components/ClickBlock.vue";
export default {
  name: "App",
  components: {
    ClickBlock,
    ResultScore,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: 0,
      end: false,
    };
  },
  methods: {
    clickHandler() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      this.end = false;
    },
    endGame(score) {
      this.score = score;
      this.isPlaying = false;
      this.end = true;
    },
  },
};
</script>

<style scopded>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  background-color: #2c3e50;
  color: whitesmoke;
  padding: 10px 30px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
button:disabled {
  cursor: not-allowed;
  background-color: #2c3e503c;
}
</style>
