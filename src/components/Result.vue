<template>
  <div class="card mt-2">
    <div class="card-body">
      <div v-if="score < 250">
        <h1 class="win">မင်းအရမ်းမြန်တယ်။! Winner</h1>
      </div>
      <div v-else-if="score > 250 && score < 500">
        <h3 class="normal">မင်းပုံမှန်ပဲ။! Normal</h3>
      </div>
      <div v-else>
        <h3>မင်းရှုံးသည်။! Loser</h3>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["score"],
};
</script>

<style scoped>
.win {
  color: #00ff11;
  user-select: none;
}
.normal {
  color: blue;
  user-select: none;
}
h3 {
  color: red;
  user-select: none;
}
</style>
