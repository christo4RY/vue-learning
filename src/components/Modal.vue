<template>
  <div class="clickHere" v-if="showModal" @click="endModal">
    <h4>အမြန်နှိပ်ပါ။</h4>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showModal: false,
      score: 0,
      timer: null,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showModal = true;
      this.startScore();
    }, this.delay);
  },
  methods: {
    startScore() {
      this.timer = setInterval(() => {
        this.score += 50;
      }, 50);
    },
    endModal() {
      clearInterval(this.timer);
      this.$emit("endGame", this.score);
    },
  },
};
</script>

<style>
.clickHere {
  display: flex;
  flex-direction: column;
  justify-content: center;
  background-color: aqua;
  width: 150px;
  height: 100px;
  margin: 20px auto;
  border: 1px solid red;
  border-radius: 10px;
}
h4 {
  color: crimson;
}
</style>
