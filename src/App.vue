<template>
  <div class="mx-auto text-center">
    <div class="card shadow-sm">
      <div class="card-body">
        <h3 class="pb-3 text-primary fw-bold">
          ဒါကို ဘယ်လောက်မြန်မြန်ဖမ်းနိုင်မလဲ။
        </h3>
        <button
          class="btn btn-warning pt-2 mb-3"
          @click="start"
          :disabled="isPlaying"
        >
          စတင်ပါ
        </button>
        <div v-if="isPlaying">
          <Modal :delay="delay" @endGame="endGame" />
        </div>
        <div v-if="resultShow">
          <Result :score="score" />
        </div>
      </div>
      <div class="card-footer">
        <div class="text-primary">&copy;2022</div>
      </div>
    </div>
  </div>
</template>

<script>
import Modal from "./components/Modal.vue";
import Result from "./components/Result.vue";
export default {
  name: "App",
  components: {
    Modal,
    Result,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: 0,
      resultShow: false,
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      this.resultShow = false;
    },
    endGame(score) {
      this.isPlaying = false;
      this.resultShow = true;
      this.score = score;
    },
  },
};
</script>

<style>
h3 {
  user-select: none;
}
</style>
