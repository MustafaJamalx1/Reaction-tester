<template>
  <div class="theme-box">
    <button id="1" class="btn" @click="themeClick(1)">ياسر</button
    ><button id="2" class="btn" @click="themeClick(2)">محمد باقر</button
    ><button id="3" class="btn" @click="themeClick(3)">حسين حمزة</button>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {
    themeClick(a) {
      this.$emit("theme", a);
    },
  },
};
</script>

<style>
.theme-box {
  display: flex;
  margin: 20px auto;
  justify-content: center;
}
.btn {
  padding: 10px;
  margin: 3px;
  font-size: 15px;
  border: 1px dotted;

  border-radius: 10px;
}
</style>
