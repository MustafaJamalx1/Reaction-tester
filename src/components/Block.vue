<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click me</div>
</template>

<script>
import { ReactiveFlags } from "vue";

export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: 0,
      reactiontime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.setTimer();
    }, this.delay);
  },
  methods: {
    setTimer() {
      this.setTimer = setInterval(() => {
        this.reactiontime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.setTimer);
      this.showBlock = false;
      this.$emit("end", this.reactiontime);
      console.log(this.reactiontime);
    },
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background-color: #0faf86;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
