<template>
  <div>
    <h1>Reaction Timer</h1>
    <button @click="playing">Start</button>
    <h1 v-if="playingStatus">You have started paying</h1>
    <BlockComp
      v-if="playingStatus"
      :delay="delay"
      @end="endGame"
      :score="score"
    />
    <ResultsComp :score="score" :status="win" />
  </div>
</template>

<script>
import BlockComp from "./components/BlockComp.vue";
import ResultsComp from "./components/ResultsComp.vue";

export default {
  name: "App",
  components: { BlockComp, ResultsComp },
  data() {
    return {
      playingStatus: false,
      score: null,
      win: false,
    };
  },

  methods: {
    playing() {
      this.delay = 2000 + Math.random() * 5000;
      console.log(this.delay);
      this.playingStatus = true;
    },
    endGame(e) {
      this.score = e;
      this.playingStatus = false;
      this.win = true;
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
button {
  padding: 13px 45px;
  border-radius: 20px;
  cursor: pointer;
  border: 1px solid black;
  transition: all 0.25s;
}
button:hover {
  transform: scale(1.09);
  background-color: rgb(234, 255, 47);
}
</style>
