<template>
  <div
    id="block"
    class="block"
    :class="{
      img1: imgUrl.imgUrl === 1,
      img2: imgUrl.imgUrl === 2,
      img3: imgUrl.imgUrl === 3,
    }"
    v-if="showBlock"
    @click="stopTimer"
    :style="{ top: top + 'px', left: left + 'px' }"
  >
    fuck me
  </div>
</template>

<script>
export default {
  props: ["delay", "imgUrl"],
  data() {
    return {
      top: 0,
      left: 0,
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
      this.top = Math.floor(Math.random() * (window.innerHeight - 300));
      this.left = Math.floor(Math.random() * (window.innerWidth - 300));
      this.setTimer = setInterval(() => {
        this.reactiontime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.setTimer);
      this.showBlock = false;
      this.$emit("end", this.reactiontime);
    },
  },
};
</script>

<style>
.block {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 200px;
  height: 200px;
  border-radius: 9999px;
  background-color: #0faf86;
  color: black;
  font-size: larger;
  text-align: center;

  background-size: cover;
  background-repeat: no-repeat;
}
.img1 {
  background-image: url(/src/assets/yasir.jpg);
}
.img2 {
  background-image: url(/src/assets/saadon.png);
}
.img3 {
  background-image: url(/src/assets/hussien.png);
}
</style>
