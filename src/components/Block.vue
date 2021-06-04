<template>
  <div class="block" v-if="blockVisible" @click="endTimer">Click Me</div>
</template>

<script>
export default {
  name: "Block",
  props: {
    delay: Number,
    timer: null,
  },
  data() {
    return {
      blockVisible: false,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.blockVisible = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    endTimer() {
      clearInterval(this.timer);
      this.blockVisible = false;
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 25rem;
  background: #0faf87;
  color: #fff;
  padding: 7rem 5rem;
  margin: 2rem auto;
  border-radius: 10px;
}
</style>