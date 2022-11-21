<template>
  <div class="block" v-if="displayBlock" @click="stopTimer">
    <p>Click Me</p>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      displayBlock: false,
      timer: null,
      score: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.displayBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.score += 50;
      }, 50);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("endGame", this.score);
    },
  },
};
</script>

<style scoped>
.block {
  width: 400px;
  height: 200px;
  border-radius: 5px;
  background-color: #2c3e50;
  text-align: center;
  color: white;
  line-height: 200px;
  margin: 50px auto;
}
</style>