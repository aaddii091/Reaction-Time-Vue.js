<template>
  <div>
    <div class="block" v-if="showBlock" @click="stopTimer">Click Me</div>
  </div>
</template>

<script>
export default {
  props: ["delay", "playingStatus", "score"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
      score1: false,
    };
  },
  mounted() {
    console.log("hi");
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      console.log(this.reactionTime);
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      console.log("hi");
      clearInterval(this.timer);
      console.log(this.reactionTime);
      this.$emit("end", this.reactionTime);
      this.score1 = true;
      this.showBlock = false;
    },
  },
};
</script>

<style>
.block {
  width: 50vw;
  padding: 100px 0;
  border: 1px solid rgb(0, 63, 0);
  border-radius: 10px;
  background-color: greenyellow;
  margin: 40px auto;
  text-align: center;
  cursor: pointer;
}
</style>
